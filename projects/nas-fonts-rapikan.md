---
type: note
title: NAS Fonts — Rencana Rapikan
---

# NAS Fonts — Rencana Rapikan

Berdasarkan audit 12 Juli 2026.

## Lokasi
`/opt/data/nas/drive-3C3A803B/Fonts/`

## Temuan
| Item | Jumlah |
|---|---|
| File font (.ttf) | Ribuan — sangat banyak |
| Font sistem (.fon) | ~200 file |
| File audio (.mp3) | Beberapa (Tulus, Virzha, Simponi, The Rain) |
| Subfolder ada | Arabic Fonts, Bugis Fonts |

## Rencana
1. Pisahkan file .mp3 ke folder `_audio/`
2. Pisahkan file .fon ke folder `_system-fonts/`
3. Kategorikan font berdasarkan jenis
4. Gunakan aturan nas-organizer: pindah ke `_trash/` jika hapus, bukan permanen
