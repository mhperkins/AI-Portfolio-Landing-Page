# MCP Server Build — Handoff
**Project:** Sprout CRM MCP Server  
**Date:** May 21, 2026  
**Status:** Ready to build — context and code design complete

---

## What This Is

An MCP (Model Context Protocol) server that wraps the Sprout CRM's live Supabase data as tools Claude can call mid-conversation. Instead of copy-pasting data into Claude, Claude queries the database itself.

Built for two reasons:
1. **Daily utility** — query the CRM conversationally from Claude Desktop
2. **Portfolio** — demonstrates Claude API tool use, multi-step reasoning, and real production data for junior AI dev roles

---

## Architecture

```
Claude Desktop (or Claude Code)
  ↕ MCP protocol (stdio)
sprout-crm MCP server (Node.js)
  ↕ Supabase SDK
Live database (one Supabase instance shared across all Sprout tools)
```

**Location:** New folder at `sprout-crm-next/mcp/`  
**Transport:** stdio — runs locally, no deployment needed  
**Connection:** Claude Desktop via `claude_desktop_config.json`

---

## Stack

```json
{
  "dependencies": {
    "@modelcontextprotocol/sdk": "^1.0.0",
    "@supabase/supabase-js": "^2.0.0",
    "dotenv": "^16.0.0",
    "zod": "^3.0.0"
  }
}
```

---

## Credentials

Already in `sprout-crm-next/.env.local`:
- `NEXT_PUBLIC_SUPABASE_URL` — the Supabase project URL
- Use the **secret key** (`sb_secret_...`) for the MCP server, not the publishable key — the MCP server runs server-side and needs to bypass RLS

---

## Tools to Expose

| Tool | What it does |
|---|---|
| `get_relationship_health` | Counts by status, overdue contacts (cadence logic), upcoming actions |
| `search_contacts` | Filter by name, status, relationship type |
| `get_contact_detail` | Full record with touchpoints and next actions |
| `list_upcoming_actions` | All next_actions due across contacts, orgs, and events |
| `list_events` | Upcoming events with contact counts |

## Resources to Expose

| Resource | Content |
|---|---|
| `sprout://profile` | Live org profile from `sprout_profile` table |
| `sprout://crm-protocol` | Reads `CRM Research Protocol.md` from the file system |

---

## Key Data Shape

Contacts live in `sprout_contacts`:
- Top-level columns: `id`, `first_name`, `last_name`, `relationship_status`, `next_action_date`, `created_at`
- `data` JSONB column contains: `touchpoints[]`, `next_actions[]`, `relationship_types[]`, `notes`, `next_action`, etc.
- Touchpoints have a `date` field used for overdue calculation

Grants live in `sprout_grants`: one row per grant, `data` JSONB is the full grant object.

Social posts live in `social_posts`: structured columns, `status` field.

Org profile lives in `sprout_profile`: single row with `id = "profile"`, `data` JSONB.

---

## The Overdue Logic

Copy this exactly — it matches what CRMManager.jsx uses:

```javascript
const CADENCE = { active: 30, warm: 90, cool: 120, cold: 180 };
const daysSince = (d) => d ? Math.floor((Date.now() - new Date(d)) / 86400000) : null;
const lastTouch = (c) => (c.touchpoints||[]).map(t=>t.date).sort().reverse()[0] || null;
const isOverdue = (c) => {
  const limit = CADENCE[c.relationship_status];
  const since = daysSince(lastTouch(c) || c.created_at?.slice(0,10));
  return limit && since !== null && since > limit;
};
```

---

## Files to Reference

| File | Why |
|---|---|
| `sprout-crm-next/lib/services.js` | Existing Supabase query functions to mirror |
| `sprout-crm-next/lib/schemas.js` | Zod schemas for all data types |
| `sprout-crm-next/lib/supabase.js` | Supabase client pattern |
| `sprout-crm-next/CRM Research Protocol.md` | Loaded as the `sprout://crm-protocol` resource |
| `sprout-crm-next/.env.local` | Credentials |

---

## Files to Create

```
sprout-crm-next/
  mcp/
    package.json    ← separate package, type: module
    server.js       ← the whole server, ~150 lines
    README.md       ← how to connect to Claude Desktop
```

---

## Claude Desktop Config (after building)

Add to `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "sprout-crm": {
      "command": "node",
      "args": ["C:/Users/maxwe/OneDrive/Desktop/Claude/Apps and Tools/sprout-crm-next/mcp/server.js"],
      "env": {
        "NEXT_PUBLIC_SUPABASE_URL": "https://ixdnmjchvjzytyhmripc.supabase.co",
        "SUPABASE_SERVICE_ROLE_KEY": "your-sb_secret_key-here"
      }
    }
  }
}
```

---

## The Demo Conversation (verify it works)

Open Claude Desktop and ask:

> "What should I focus on this week for relationships?"

Claude should:
1. Call `get_relationship_health`
2. Call `search_contacts` or `list_upcoming_actions`
3. Read `sprout://profile` for org context
4. Respond with a specific, prioritized answer grounded in live data

That sequence is the portfolio demo.

---

## Portfolio Sentence (use this when describing the project)

> "I built an MCP server on top of a production CRM that exposes live contact and relationship data as Claude tools. Claude queries the database mid-conversation, identifies relationship gaps using custom cadence logic, and generates research briefs following the protocol I wrote — all from a single conversation."

---

## Context from Previous Work

- The n8n weekly digest automation was built first (same session) and is now live and published. It runs every Monday 8am. The MCP server is separate — no connection between them.
- One Supabase instance serves all three Sprout tools (CRM, Grant Manager, Social Manager).
- RLS is enabled. Use the service role secret key in the MCP server to bypass it.
- The CRM Research Protocol markdown file is at `sprout-crm-next/CRM Research Protocol.md` and is the primary resource to expose — it contains the full 7-phase research protocol plus Claude prompt templates.
