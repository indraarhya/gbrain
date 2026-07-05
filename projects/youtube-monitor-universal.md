---
type: project
title: YouTube Monitor — Universal
status: active
tags:
  - automation
  - cron
  - fallback
  - template
  - youtube
---

## Script Universal
`scripts/yt-monitor.py` — monitor channel YouTube manapun. Terima argumen:
- `--channel` (required): YouTube channel ID
- `--name`: Nama channel (untuk output)
- `--podcast-rss`: URL RSS podcast (opsional, untuk show notes lebih kaya)

## Fallback Chain
1. ASR (yt-dlp) → auto-captions
2. YouTube API (OAuth) → caption tracks
3. Podcast RSS (opsional) → show notes
4. Description (yt-dlp) → episode notes

## State File
Tiap channel punya state sendiri di `cron/yt-monitor/{channel_id}.txt`

## Cara Nambah Channel Baru
1. Buat wrapper script (copy pola `scripts/acquired-monitor.py`)
2. Ganti parameter `--channel`, `--name`, `--podcast-rss`
3. Buat cron job tiap 2 jam

Atau langsung dari cron prompt: jalankan `python3 ~/.hermes/scripts/yt-monitor.py --channel UC... --name "Nama"`

## Format Rangkuman
🎙️ title | 📅 date | 🔗 url | ⏱ duration
--- 🔥hook --- 📖Konteks --- 📌Poin Utama --- 🎯Kesimpulan --- ⏱Chapter(tabel) --- 💡Quote --- 📚Referensi
Pemisah: ---. Tabel hanya untuk chapter. Bahasa Indonesia santai.
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing