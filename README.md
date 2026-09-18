# Detour for Claude

This is the public Claude plugin distribution package for [Detour](https://detour.discomedia.co), a hosted service for creating and maintaining private maps. It connects Claude Code and Claude Cowork to Detour's production remote MCP server; it contains no local server, API key, backend source, or user credentials. Standard Claude Chat does not execute installed plugins.

## What it does

Use Detour to create and organize private maps and save researched places with coordinates, public descriptions, addresses, hours, source URLs, and Google Maps place permalinks. Research remains in your client; Detour stores only the places you choose to save.

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
