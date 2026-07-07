---
type: note
title: Update Arsitektur VPS — 6 Juli 2026
---

# Update Arsitektur VPS — 6 Juli 2026

Berdasarkan Arsitektur-VPS.md terbaru.

## Perubahan dari Versi Sebelumnya

| Item | Sebelum | Sesudah |
|---|---|---|
| Saldo DeepSeek | $2.82 | **$5.17** (top-up 6 Juli) |
| Model utama Clawndra | GPT-5.4 (9Router) | **DeepSeek v4-flash** |
| Fallback chain | — | v4-flash → v4-pro → gpt-4o |
| Gemini akses | Diblok (via Cloudflare) | ✅ **Langsung** dari VPS |
| Backup | Hermes & 9Router belum | ✅ **Sudah termasuk** |
| Gotcha | 16 item | **17 item** (+gbrain-bridge force-recreate) |

## Detail Perubahan

### Saldo & Model
- DeepSeek di-top-up ke $5.17 (dari ~$0.93)
- Clawndra sekarang pake DeepSeek v4-flash sebagai primary

### Gemini
- Sebelumnya diblok dari IP VPS → harus via Cloudflare AI Gateway
- Sekarang **bisa langsung** — dipakai OpenClaw untuk embedding internal

### Backup (sudah lengkap)
- pg_dump: n8n + gbrain-db (brain bersama)
- tar: /data/{n8n, clawndra, hermes, 9router}
- Config: compose.yaml, compose.override.yaml, .env
- Cron: 02:00 WITA, rclone → Google Drive
