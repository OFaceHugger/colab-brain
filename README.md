# 🧠 Chimera Colab Brain v7.2.1 — UNLEASHED

Mirror of `ScottzillaSystems/colony/colab_brain.ipynb` — hosted here so Google Colab's
**GitHub open format** works reliably (Colab's `#fileUrl` fragment is deprecated).

## 🚀 Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/OFaceHugger/colab-brain/blob/main/colab_brain.ipynb)

> Click the badge → **Runtime → Restart session** → **Run All**.
> (Restarting the session reloads this notebook fresh — a cached tab still runs the old version.)

## What it does

Auto-VRAM tier dispatch on Colab GPU. **v7.2 = the T4 tier now runs an ABLITERATED
(uncensored) model.**

| VRAM | Backend | Model | Alias | Uncensored |
|------|---------|-------|-------|-----------|
| >=70GB | llama.cpp | DeepSeek-R1-Distill-Llama-70B Q5_K_M (46GB) | deepseek-r1-llama-70b | — |
| >=40GB | llama.cpp | DeepSeek-R1-Distill-Qwen-32B Q4_K_M (20GB) | deepseek-r1-qwen-32b | — |
| >=14GB | llama.cpp | **huihui Qwen3-14B-abliterated Q4_K_M (9.0GB)** | qwen3-14b | ✅ |
| else | transformers | Qwen3-30B-YOYO 4-bit | qwen3-30b-yoyo-opus | — |

- **T4 (15GB) tier:** `bartowski/huihui-ai_Qwen3-14B-abliterated-GGUF` → `huihui-ai_Qwen3-14B-abliterated-Q4_K_M.gguf`
  (refusal-removal of Qwen3-14B — same size, same native tool-calling XML the parser handles.)
- TPU v5e is NOT supported (no CUDA / no llama.cpp backend). Select **T4**.
- Sovereign bearer-key gate, global request cap, flat usage log, thinking/tool-call split,
  reverse tunnel to VPS :8898, colony :8766 registration. No hardcoded secrets.

## Setup (one time)

Colab secrets (key icon → Add new secret):
- `COLONY_TOKEN` — cat /opt/chimera/colony_token.txt on VPS
- `AGENT_PASS` — colab ssh password
- `BRAIN_API_KEY` — openssl rand -hex 24

Then Runtime → Restart session → Run All. Expect `[TIER] 14b` + Cell 5: READY FOR STRIX.

## Changelog

- **v7.2.1** — FIX: MODEL_ID defined in every VRAM tier (was NameError on GGUF tiers → /v1/models 500)
- **v7.2** — T4 tier → huihui Qwen3-14B-**abliterated** Q4_K_M (uncensored, bartowski quant)
- **v7.1.1** — fixed T4 tier GGUF repo (lm-kit/qwen-3-14b-instruct-gguf, verified real)
- **v7.1** — added T4-class tier (Qwen3-14B Q4_K_M via llama.cpp)
- **v7.0** — bearer-key gate, secrets out of notebook, global cap + usage log, watchdog hardening

## Canonical source

HF: `ScottzillaSystems/colony` → `colab_brain.ipynb` (same bytes). This repo is a mirror for
Colab-open reliability only; the HF Space is the source of truth.
