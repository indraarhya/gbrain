---
type: note
title: Cron Jobs & Automasi
---

# Cron Jobs & Automasi

| Nama | Jadwal (UTC) | Tujuan | Status |
|---|---|---|---|
| Berita AI Harian | 22:00 | 📰 Berita AI (topic 19) | ✅ |
| Berita Otomotif | 06:00 | 🚗 Otomotif (topic 31) | ✅ |
| gbrain sync | 00:30/06:30/12:30/18:30 | Local (silent) | ✅ |
| gbrain MCP watchdog | Tiap 10 menit | Local (silent) | ✅ |
| gbrain auto-commit | 23:00 | Local (silent) | ✅ |
| DeepSeek monitor | 00:00/06:00/12:00/18:00 | Origin (notif) | ✅ |

## Script
- `/opt/data/scripts/gbrain-sync.sh` — sync dengan stop/start MCP
- `/opt/data/scripts/gbrain-mcp.sh` — watchdog MCP
- `/opt/data/scripts/gbrain-autocommit.sh` — auto commit & push ke GitHub
- `/opt/data/scripts/deepseek-monitor.sh` — monitor saldo DeepSeek
