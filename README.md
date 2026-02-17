# Magicline API Reference Skill

A Claude-compatible documentation skill for the Magicline API ecosystem.

This repository packages a practical skill prompt (`SKILL.md`) together with synced endpoint documentation for:
- Magicline OpenAPI
- Magicline Connect API
- Magicline Device API

## Repository Contents

- `SKILL.md` – primary skill instructions and API usage guidance for Claude
- `references/magicline/` – synced markdown reference docs and metadata for all supported APIs
- `CLAUDE.md` – local assistant context/history metadata

## What This Project Is For

Use this project when you want Claude to:
- understand the Magicline API landscape quickly
- select the correct API for a use case (OpenAPI vs Connect vs Device)
- reference endpoint-level documentation while drafting integrations
- follow common patterns such as preview/execute and dry-run flows

## Getting Started

1. Open `SKILL.md` and load it into your Claude workflow as your skill prompt/context.
2. Keep the `references/magicline/` folder available so endpoint-specific markdown can be resolved.
3. Ask Claude integration questions (e.g. endpoint selection, request/response design, validation and error handling).

## Source of Reference Documentation

The reference corpus is synced from:
- `https://redocly.sportalliance.com/apis/magicline/openapi/openapi.md`
- `https://redocly.sportalliance.com/apis/magicline/connectapi/connectapi.md`
- `https://redocly.sportalliance.com/apis/magicline/deviceapi/deviceapi.md`

Metadata about sync state is stored in:
- `references/magicline/_state.json`
- `references/magicline/_manifest.json`

## Maintenance Notes

- This repository is documentation-focused and currently has no build/test pipeline.
- Keep `SKILL.md` aligned with changes to the synced references.
- Avoid editing generated reference pages unless you are intentionally updating synced content.
