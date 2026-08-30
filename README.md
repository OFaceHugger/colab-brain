# 🧠 Chimera Colab Brain v7.1

Mirror of `ScottzillaSystems/colony/colab_brain.ipynb` — hosted here so Google Colab's
**GitHub open format** works reliably (Colab's `#fileUrl` fragment is deprecated).

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/OFaceHugger/colab-brain/blob/main/colab_brain.ipynb)

## What it does

Auto-VRAM tier dispatch on Colab GPU (v7.1 adds the T4-class tier):

| VRAM | Backend | Model | Alias |
|------|---------|-------|-------|
| >=70GB | llama.cpp | DeepSeek-R1-Distill-Llama-70B Q5_K_M (46GB) | deepseek-r1-llama-70b |
| >=40GB | llama.cpp | DeepSeek-R1-Distill-Qwen-32B Q4_K_M (20GB) | deepseek-r1-qwen-32b |
| >=14GB | llama.cpp | Qwen3-14B-Instruct-2507 Q4_K_M (9.2GB) — T4-class | qwen3-14b |
| else | transformers | Qwen3-30B-YOYO 4-bit | qwen3-30b-yoyo-opus |

Sovereign bearer-key gate, global request cap, flat usage log, thinking/tool-call split,
reverse tunnel to VPS :8898, colony :8766 registration. No hardcoded secrets.

## Setup (one time)

Colab secrets (key icon → Add new secret):
- `COLONY_TOKEN` — cat /opt/chimera/colony_token.txt on VPS
- `AGENT_PASS` — colab ssh password
- `BRAIN_API_KEY` — openssl rand -hex 24

Then Runtime → Restart session → Run All. Expect `[TIER]` line + Cell 5: READY FOR STRIX.

## Canonical source

HF: `ScottzillaSystems/colony` → `colab_brain.ipynb` (same bytes). This repo is a mirror for
Colab-open reliability only; the HF Space is the source of truth.
