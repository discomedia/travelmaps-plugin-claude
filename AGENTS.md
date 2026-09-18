# Detour Claude plugin distribution guide

This public repository is the distribution-only Claude plugin for Detour. It is
part of the Detour product, but the canonical backend, OAuth implementation,
MCP domain services, production operations, and product documentation remain
in the private `discomedia/travelmap` repository.

## Boundaries

- Keep this repository limited to the Claude plugin manifest, hosted MCP
  connection, public documentation, and distributable assets.
- Do not copy backend source, database code, authentication implementation,
  private test fixtures, production IDs, access tokens, or credentials here.
- The only production connection is `https://api.detour.discomedia.co/mcp`.
  A package change must not change that endpoint, its OAuth requirements, or
  its tool contract without a separately reviewed and verified backend release.
- Keep user-facing copy accurate: Detour creates and maintains private maps;
  map mutations remain subject to the server's authorization, versioning, and
  destructive-operation confirmation safeguards.

## Validation and release

Use `main` as the default branch. GitHub stores and distributes this package;
pushing here does not deploy the Detour backend. Before committing, validate
the JSON manifests, referenced assets, and endpoint value, then run `git diff
--check`. When an authenticated Claude Code installation is available, also run
the current official plugin validation and install flow; do not install software
or submit/publish a marketplace listing without explicit owner authorization.

Update this README and the private repository's relevant product and operations
documentation whenever the public distribution, plugin contract, authentication
requirements, or support/privacy links change.
