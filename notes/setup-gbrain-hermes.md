---
type: note
title: Setup gbrain & Hermes
---

# Setup gbrain & Hermes

## Instalasi (3 Juli 2026)
- Bun 1.3.14, gbrain 0.42.56.0
- Brain PGLite (lokal, tanpa server), 117 migrasi
- Schema: gbrain-base-v2
- 68 skill gbrain di-scaffold ke ~/.hermes/skills/
- 94 tools MCP teregistrasi di Hermes

## MCP Server
- Port 3131, HTTP MCP dengan OAuth
- Token: gbrain_a5444aabebfedf100109d610e640b55b34bad9dc4eb805620ddd7531fdf51298
- Watchdog: script /opt/data/scripts/gbrain-mcp.sh, cron tiap 10 menit

## PGLite Limitation
- Single-writer — hanya 1 proses bisa akses DB
- Sync script matiin MCP → sync → nyalain MCP otomatis

## GitHub
- Repo: https://github.com/indraarhya/gbrain
- 9 commit, auto-commit tiap hari jam 23:00 UTC
- Template folder: companies/, projects/, concepts/
