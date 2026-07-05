---
type: note
title: Arsitektur VPS — Clawndra + Hermira
---

# Arsitektur VPS — Clawndra + Hermira

Berdasarkan dokumen Arsitektur-VPS.md (2026-07-06)

## Infrastruktur
- Provider: SumoPod (Tencent, Jakarta)
- OS: Ubuntu 24.04, 2 vCPU / 3.6 GB RAM / 60 GB
- Domain: indraarhya.id (Cloudflare)
- Akses: Cloudflare Tunnel (egress-only) + Tailscale (admin privat)

## Stack Docker (~/clawndra/)
| Service | Fungsi |
|---|---|
| **Clawndra** (OpenClaw) | Agent AI #1, dashboard claw.indraarhya.id |
| **Hermira** (Hermes) | Agent AI #2, dashboard hermes.indraarhya.id |
| **n8n** | Workflow automation, n8n.indraarhya.id |
| **9Router** | Router LLM, 9router.indraarhya.id |
| **Postgres** | Database n8n |
| **Cloudflared** | Tunnel Cloudflare |

## Dua Agent
| | Clawndra | Hermira |
|---|---|---|
| Platform | OpenClaw | Hermes Agent |
| LLM | GPT-5.4 (via 9Router) + DeepSeek | DeepSeek |
| Fitur | Telegram | Telegram + Google (Gmail/Calendar/Drive) |
| Brain | — | ✅ gbrain MCP (port 3131) |

## Pembaruan 6 Juli 2026
- Fix: home_channel dari string jadi objek (crash gateway)
- Semua cron OK kembali
