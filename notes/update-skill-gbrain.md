---
type: note
title: Update Skill gbrain + Kontrak Agent
---

# Update Skill gbrain + Kontrak Agent (2026-07-06)

## Skill Baru di /opt/data/skills/
38 skill gbrain sudah dipasang di direktori skill Hermes, termasuk:
- brain-ops, query, enrich, ingest, maintain
- briefing, daily-task-manager, daily-task-prep
- citation-fixer, cron-scheduler
- signal-detector, idea-ingest, media-ingest, meeting-ingestion
- book-mirror, strategic-reading, article-enrichment
- academic-verify, concept-synthesis
- archive-crawler, brain-pdf, cross-modal-review
- gbrain-advisor, soul-audit
- skill-creator, skillify
- testing, reports, webhook-transforms
- Dan lainnya + file kontrak

## Kontrak Baru (_AGENT_README.md)
1. Brain-first: cek brain sebelum aksi eksternal
2. File by primary subject (org→people/, perusahaan→companies/)
3. No slop: tanpa filler phrases
4. Deterministic links: jangan tebak URL
5. Shared brain: Postgres bersama Clawndra
