---
type: note
title: Telegram Topic Mapping
tags:
  - config
  - forum-topics
  - telegram
---

# Mapping Topic Telegram — Grup Hermes Agent

| Thread ID | Nama Topic | Fungsi |
|-----------|-----------|--------|
| 1 | General | Umum, sapaan, random |
| 19 | **AI & Technology** | Berita AI harian + diskusi AI/tech |
| 20 | Coding | Diskusi coding & config |
| 21 | Mobile Legend | Game MLBB |
| 23 | Sepakbola | Diskusi bola & Piala Dunia 2026 |
| 31 | Otomotif | Berita otomotif harian |
| 356 | **GitHub** | Repo, coding projects, GitHub workflows |

> **Catatan:** Topik **Bisnis & Target** (ID 25) sudah tidak ada. Digantikan oleh topik **GitHub** (ID 356).

## Konfigurasi
- **Cron Berita AI Harian** → deliver ke topic 19 ✅
- **Cron Berita Otomotif** → deliver ke topic 31 ✅
- **Group ID**: -1003945902613
- **Bot**: @hermira_id_bot
- **Akses Telethon (user)**: Aktif — bisa getForumTopics via MTProto

## Setup Terakhir
- 5 Juli 2026: QR login berhasil, 2FA teratasi
- Session file: `/opt/data/home/telethon-env/user-session.session`
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing