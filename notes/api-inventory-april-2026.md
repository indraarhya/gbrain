---
type: note
title: API Inventory — Hermes Agent Indra
created: '2026-07-05T00:00:00.000Z'
tags:
  - api
  - config
  - cost
  - infrastructure
---

# API Inventory — Hermes Agent

Semua API yang digunakan di agent Hermes milik Indra.

## API Aktif (berfungsi penuh)

### DeepSeek
- **Model:** deepseek-v4-flash
- **Endpoint:** `https://api.deepseek.com/v1`
- **Biaya:** $0.09/1M input tokens, $0.18/1M output tokens
- **Saldo:** $1.76 (top-up, per 5 Juli 2026)
- **Key:** Dari `/opt/data/.env` via env var `DEEPSEEK_API_KEY`
- **Status:** ✅ Aktif — dipakai tiap chatting

### Brave Search API
- **Tier:** free (backend `brave-free` di config)
- **Biaya:** $5 kredit gratis/bulan (~1.000 query gratis)
- **Key:** `BSABLEw92jwxz6GoyT29E_sbENSbzT6` dari `/opt/data/.env`
- **Status:** ✅ Aktif — dipakai untuk web_search

### Google Workspace
- **Fungsi:** Gmail, Calendar, Drive, Docs, Sheets via OAuth
- **Biaya:** Gratis (akun Google Workspace org)
- **Status:** ✅ Aktif

### Telegram Bot API
- **Bot:** @hermira_id_bot
- **Token:** 8701098041:*** dari `/opt/data/.env`
- **Home group:** Hermes Agent (-1003945902613)
- **Biaya:** Gratis total
- **Status:** ✅ Aktif

### Telegram MTProto (Telethon)
- **Akun:** Indra (ID 263540728)
- **Session:** `/opt/data/home/telethon-env/user-session.session`
- **API ID/Hash:** 36677878 / 83806c1c319ce9f872dce0f31285e093
- **Biaya:** Gratis total
- **Status:** ✅ Aktif

### WhatsApp Baileys Bridge
- **Endpoint:** `http://127.0.0.1:3000`
- **Script:** `/opt/data/whatsapp-bridge/ai-agent-v3.py`
- **Biaya:** Gratis (unofficial bridge, lokal)
- **Status:** ✅ Aktif

### gbrain MCP Server
- **Endpoint:** `http://localhost:3131/mcp`
- **Auth:** Bearer token dari env `MCP_GBRAIN_API_KEY`
- **Engine:** PGLite lokal
- **Biaya:** Gratis total (lokal)
- **Status:** ✅ Aktif

## API Belum Aktif

### OpenAI Whisper (STT)
- **Sudah di config** (model: whisper-1)
- **Biaya:** $0.006/menit audio (~$0.36/jam)
- **Status:** ❌ Belum ada key

### X/Twitter API (xurl)
- **CLI:** `~/.local/bin/xurl`
- **Status:** ❌ Belum OAuth

### ZeroEntropy / OpenAI Embedding
- **Untuk semantic search di gbrain**
- **Biaya:** Berbayar
- **Status:** ❌ `embedding_disabled: true` — belum punya key

## Catatan Biaya

- Hanya **DeepSeek** yang beneran mengeluarkan biaya saat ini
- Brave Search gratis sampai ~1.000 query/bulan
- Sisanya gratis total
- Monitor DeepSeek lewat cron tiap 6 jam: notifikasi jika terpakai >=$1 atau sisa <=$0.50
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing