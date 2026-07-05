---
type: reference
title: 9Router Setup Guide — Dashboard & API
updated: '2026-07-05T00:00:00.000Z'
tags:
  - 9router
  - api
  - llm
  - proxy
---

# 9Router Setup Guide

## Akses
- **URL:** https://9router.indraarhya.id
- **Auth:** Cloudflare Access (email OTP) — indra.harry@gmail.com
- **Service internal:** http://ninerouter:20128 (dari dalam Docker network)

## Langkah — Dashboard

### 1. Buat API Key
- Masuk dashboard → Settings / API Keys
- Create Key → beri nama (misal: `indra-main`)
- Copy & simpan key-nya (hanya muncul sekali)

### 2. Buat Combo (Route)
- Menu Combos / Routes → Create Combo
- Nama combo: bebas (misal: `indra-ai`) — ini jadi `model` parameter
- Tambah models urut prioritas (auto-fallback):
  1. kr/claude-sonnet-4.5 (Claude 4.5 free via Kiro)
  2. vertex/gemini-2.5-pro ($300 credit Google Cloud)
  3. kr/glm-5 (GLM-5 free via Kiro)
  4. opencode/free (OpenCode free)
- Save

### 3. Tes API
```bash
curl https://9router.indraarhya.id/v1/chat/completions \
  -H "Authorization: Bearer ***" \
  -H "Content-Type: application/json" \
  -d '{"model": "<nama-combo>", "messages": [{"role": "user", "content": "Halo"}]}'
```

## Integrasi ke OpenClaw
Tambah provider di config OpenClaw:
```json
"openai": {
  "base_url": "http://ninerouter:20128/v1",
  "api_key": "***"
}
```

## Integrasi ke Tool Lain
| Tool | Base URL | Model |
|------|----------|-------|
| Claude Code | http://localhost:20128/v1 | cc/claude-opus-4-7 |
| Codex CLI | export OPENAI_BASE_URL=http://localhost:20128/v1 | — |
| Cline (VS Code) | OpenAI Compatible → http://...:20128/v1 | combo name |
| Hermes | config.yaml → custom provider | combo name |
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing