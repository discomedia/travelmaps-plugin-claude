# Detour for Claude

This is the public Claude plugin distribution package for [Detour](https://detour.discomedia.co), a hosted service for creating and maintaining private maps. It connects Claude Code and Claude Cowork to Detour's production remote MCP server; it contains no local server, API key, backend source, or user credentials. Standard Claude Chat does not execute installed plugins.

## What it does

Use Detour to create and organize private maps and save researched places with coordinates, public descriptions, addresses, hours, source URLs, and Google Maps place permalinks. Research remains in your client; Detour stores only the places you choose to save.

After a map read or successful content change, Detour returns a portrait map
preview. MCP Apps-capable clients render it inline; other compatible clients
receive the same preview as standard MCP image content. The preview is
display-only and does not add a browser-based editing surface.

The plugin starts the browser-based Detour OAuth flow when access is needed. Approve `maps:read` to view your maps and `maps:write` to create or change them. `offline_access` lets a compatible client renew an approved session without asking you to sign in again.

Detour never asks Claude to provide a password, MFA code, API key, or Google Maps credential.

## Development and validation

This repository is distribution-only. The canonical Detour backend, OAuth implementation, operational runbooks, and product documentation live in a separate private repository. Do not add backend source, secrets, test accounts, or production credentials here.

Validate the manifests and assets before committing. When an authenticated Claude Code installation is already available, use its current official plugin validation and local install workflow. This package connects to:

```
https://api.detour.discomedia.co/mcp
```

## Safety, support, and privacy

Map creation and updates are idempotent and versioned. Targeted removal,
clearing a map, archiving, and permanently deleting an archived map require a
preview followed by explicit confirmation. The server checks ownership, OAuth
scope, preview tokens, and current versions before it applies a destructive
change.

- [Product site](https://detour.discomedia.co)
- [Support](https://detour.discomedia.co/support)
- [Privacy](https://detour.discomedia.co/privacy)
- [Terms](https://detour.discomedia.co/terms)

For support, include the client, Detour tool name, and a concise description of
the result. Never send access tokens or passwords.


## Tool permissions and destination privacy

The server exposes 17 tools, including atomic create/edit/archive/purge batches.
Reading maps, searching saved places, and listing maps do not create an account
profile or update its activity timestamp. Editing fields is labeled destructive
because prior values cannot be restored with an undo action; edits still require
map versions and idempotency keys. Removal, clear, archive and purge retain
preview/confirmation safeguards.

Coordinates and addresses describe destinations you explicitly choose to save,
not your current/device location or a request for your home/work address.
Preview-producing tools are labeled open-world: the server sends the computed
center, zoom and image settings to LocationIQ. For a single pin the center can
identify that destination. Map titles, notes, account identity and marker lists
are not sent. Batch tools do not render images or contact LocationIQ. See the
[privacy policy](https://detour.discomedia.co/privacy) for retention and deletion.
