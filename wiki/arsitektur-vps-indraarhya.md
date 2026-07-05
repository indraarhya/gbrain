---
type: reference
title: Arsitektur VPS — Clawndra + Hermira + n8n + 9Router
updated: '2026-07-05T00:00:00.000Z'
tags:
  - cloudflare
  - docker
  - infrastructure
  - sumopod
  - vps
---

# Arsitektur VPS — Clawndra + Hermira + n8n + 9Router (indraarhya.id)

## TL;DR
Satu VPS SumoPod menjalankan **Docker Compose** dengan **6 service**. Tidak ada port publik — semua lewat **Cloudflare Tunnel** (egress-only) + **Cloudflare Access** (email OTP). Otak LLM utama = **DeepSeek**.

## VPS Specs
- **Provider:** SumoPod (Tencent, Jakarta)
- **IP:** 43.157.230.247
- **OS:** Ubuntu 24.04 LTS
- **Spec:** 2 vCPU / 3.6 GB RAM / 60 GB disk + swap ~4 GB
- **TZ:** Asia/Makassar (WITA, UTC+8)
- **SSH:** user `ubuntu`, port 22
- **Stack dir:** `~/clawndra/`

## Cloudflare Setup
- **Domain:** indraarhya.id (registrar Rumahweb → NS Cloudflare)
- **Account ID:** 600bf17307d226432fd76324096dc558
- **Tunnel:** `clawndra` — egress-only, no inbound ports
- **Access:** Zero Trust, tim `indraarhya`, email OTP (indra.harry@gmail.com)
- **AI Gateway:** proxy Gemini (bypass geo-block dari IP VPS)

## Subdomain Publik (4 app)

| Subdomain | Target | Layanan |
|-----------|--------|---------|
| n8n.indraarhya.id | http://n8n:5678 | n8n |
| claw.indraarhya.id | http://openclaw:18789 | Clawndra (OpenClaw) |
| 9router.indraarhya.id | http://ninerouter:20128 | 9Router dashboard |
| hermes.indraarhya.id | http://hermes:9119 | Hermira (Hermes) + basic-auth |

## Docker Stack

| Service | Image | Port | Volume |
|---------|-------|------|--------|
| postgres | postgres:16 | 5432 | /data/postgres |
| n8n | n8nio/n8n | 5678 | /data/n8n |
| cloudflared | cloudflare/cloudflared | — | — |
| openclaw | ghcr.io/openclaw/openclaw | 18789 | /data/clawndra |
| ninerouter | decolua/9router:0.5.12 | 20128 | /data/9router |
| hermes | nousresearch/hermes-agent | 8642(API)/9119(dash) | /data/hermes |

Compose files: `compose.yaml` (inti) + `compose.override.yaml` (auto-merge). JANGAN edit compose.yaml langsung.

## Dua Agent AI

| Aspek | Clawndra (OpenClaw) | Hermira (Hermes) |
|-------|---------------------|-------------------|
| Container | clawndra-openclaw-1 | hermes |
| Dashboard | claw.indraarhya.id:18789 | hermes.indraarhya.id:9119 |
| LLM | DeepSeek v4-flash (primary) | DeepSeek (custom provider) |
| Channel | Telegram | Telegram + Google (Gmail/Calendar/Drive) |

## LLM Layer
- **Default:** DeepSeek (murah ~$0.14/1M input)
- **OpenClaw models:** deepseek/deepseek-v4-flash (primary), fallback: chat, v4-pro, reasoner
- **OpenClaw providers:** openai → 9Router, google → Gemini via CF AI Gateway
- **Hermes model:** custom → api.deepseek.com, model: deepseek-chat
- ⚠️ **DeepSeek deprecation:** deepseek-chat/reasoner deprecated 24 Juli 2026 — migrasi ke v4-flash

## Keamanan
- Cloudflare Access (email OTP) di depan semua UI
- Hermes dashboard: Access + basic-auth
- UFW: SSH only. fail2ban aktif.
- openclaw container: cap_drop ALL, no-new-privileges, non-root

## Backup
- `~/clawndra/backup.sh`: pg_dump n8n + tar /data/{n8n,clawndra} + compose.yaml & .env
- Retensi 7 hari, cron 02:00 WITA
- Off-site: rclone → Google Drive (gdrive:clawndra-backup)
- ⚠️ **TODO:** tambah /data/hermes & /data/9router ke backup

## Gotchas
1. Edit openclaw.json hanya via jq/CLI (auto-restore)
2. gateway.bind OpenClaw = lan (bukan loopback)
3. Restart cloudflared setiap restart openclaw
4. Gemini diblok dari IP VPS → wajib CF AI Gateway
5. Hermes SOUL.md dibaca saat sesi mulai → butuh /new setelah ganti persona
6. /data/hermes milik user hermes → host ubuntu "permission denied" saat ls = normal
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing
[db-disconnect-audit] write failed (EACCES: permission denied, open); continuing