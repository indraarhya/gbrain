---
type: project
title: Acquired FM Watcher
status: active
tags:
  - automation
  - cron
  - fallback
  - youtube
---

## Fallback Chain

1. **ASR** (yt-dlp) → auto-captions
2. **YouTube API** (OAuth) → manual captions
3. **Podcast RSS** (Transistor.fm `https://feeds.transistor.fm/acquired`) → show notes
4. **Description** (yt-dlp) → episode notes

## Credentials
- YouTube cookies: `credentials/youtube-cookies.txt`
- YouTube OAuth: `credentials/youtube-token.json`
- Deno JS runtime: `~/.local/bin/deno`

## Script
`scripts/acquired-fetch.py` — deteksi video baru via RSS YouTube, fallback chain extract content.

## Cron
Tiap 2 jam. Job: "Acquired FM - Rangkuman"

## Format Rangkuman Final
🎙️ title | 📅 date | 🔗 url | ⏱ duration
---🔥hook---📖Konteks---📌Poin Utama---🎯Kesimpulan---⏱Chapter(tabel)---💡Quote---📚Referensi
Pemisah: --- . Tabel hanya untuk chapter. Bahasa Indonesia santai.
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing