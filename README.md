---
title: "Mitigating Shortcut Learning in Brain Tumour MRI Classification"
emoji: 🧠
colorFrom: teal
colorTo: blue
sdk: docker
app_port: 8080
header: mini
pinned: false
tags:
  - research-article-template
  - medical-imaging
  - explainable-ai
  - vision-transformers
---

# Mitigating Shortcut Learning in Brain Tumour MRI Classification

The web-native research article for Riya Basak's BSc Artificial Intelligence project at the University of Hertfordshire.

This repository uses the official [Hugging Face research article template](https://huggingface.co/spaces/tfrere/research-article-template), the same article system used by [CorrSteer](https://seonglae-corrsteer.hf.space/). The scientific narrative is derived from the submitted FYP report and the accompanying implementation repository.

## Evidence boundary

- Dataset: 6,726 unique images after exact SHA1 deduplication.
- Held-out test set: 1,284 images.
- Best classifier: Ablation B, 99.22% accuracy and 0.9920 macro-F1.
- Best qualitative Grad-CAM++ localisation among the three reported cases: Hybrid B, 3/3.
- The localisation count is not a full-test-set metric.
- The study has no external clinical validation, tumour masks, or formal calibration analysis.
- This is a final-year research project, not a peer-reviewed clinical study or medical device.

## Edit the article

| Path | Purpose |
| --- | --- |
| `app/src/content/article.mdx` | Article metadata and chapter order |
| `app/src/content/chapters/` | Research narrative |
| `app/src/content/embeds/` | Interactive banner and scientific charts |
| `app/src/content/assets/data/` | Machine-readable result tables |
| `app/src/content/assets/image/` | Report-generated figures |
| `app/src/content/bibliography.bib` | Cited references |
| `VALIDATION_PLAN.md` | Preregistered evidence-upgrade requirements |

## Run locally

```bash
cd app
npm install
npm run dev
```

Production build:

```bash
cd app
npm run build
```

## Primary resources

- [Model and experiment repository](https://github.com/AnnyaB/HybridResNet50V2-RViT)
- [Interactive model demo](https://huggingface.co/spaces/AnnyaaB/brain-tumour-pfd-gste-demo)
- [PFD–GSTE package](https://pypi.org/project/pfd-gste/)

## Attribution and reuse

The article interface remains attributed to the official research article template. Repository code and third-party assets retain their respective licences. The clinical disclaimer and evidence limitations must remain visible in redistributed versions.
