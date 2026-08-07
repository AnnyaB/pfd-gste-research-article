# Evidence Upgrade Protocol

This protocol defines the evidence required to strengthen the PFD–GSTE article without retrofitting claims to favourable outcomes. It is a forward-looking plan, not a source of completed results.

## Non-negotiable rules

1. Preserve the fixed, leakage-audited development split and publish its manifest hash.
2. Fit models, thresholds, and calibration transforms using training and validation data only.
3. Evaluate the held-out test set only after checkpoint selection is complete.
4. Preserve every planned seed and failed run in the run manifest; do not omit unfavourable outcomes.
5. Compare guidance only within matched A and B families unless all non-guidance factors are controlled.
6. Release the exact predictions used for every reported aggregate, subject to dataset licensing constraints.

## 1. Repeated-seed study

- Seeds: `42, 123, 456, 789, 2026`.
- Variants: Hybrid A, Ablation A, Hybrid B, Ablation B.
- Shared settings: identical split files, augmentation, batch size, loader policy, early-stopping rule, optimiser, scheduler, and determinism configuration.
- Primary comparison: guided versus unguided macro-F1 within each architecture family.
- Secondary measures: accuracy, loss, specificity, Cohen's kappa, MCC, and absolute error count.
- Reporting: per-seed values, mean, standard deviation, 95% confidence interval, paired family delta, and complete run manifest.

Required table schema:

```text
model,family,guided,seed,split_manifest_sha256,best_epoch,accuracy,macro_f1,loss,specificity,kappa,mcc,errors
```

## 2. Calibration study

Save one row per image with its stable sample identifier, true class, predicted class, four class probabilities, checkpoint hash, and seed.

Report:

- negative log-likelihood;
- multiclass Brier score;
- expected calibration error with the binning rule declared in advance;
- classwise reliability diagrams and sample counts per bin;
- uncalibrated and temperature-scaled results, with temperature fitted on validation predictions only;
- selective accuracy or risk–coverage curves if abstention is discussed.

MC Dropout variation remains a separate stochastic-uncertainty analysis and must not be presented as calibration by itself.

## 3. External validation

An external cohort is eligible only if:

- its provenance is documented;
- it was not used to construct the Nickparvar aggregate benchmark;
- exact and near-duplicate screening finds no overlap with development data;
- acquisition sequence and class mapping are defensible;
- licensing permits the intended evaluation and release of derived statistics.

The existing five-image meningioma sample is a qualitative demonstration and must not be promoted to a formal benchmark. If a defensible four-class mapping cannot be established, report a narrower task explicitly rather than forcing incompatible labels.

## 4. Quantitative localisation

Define a held-out localisation subset before inspecting model maps. Use tumour masks created or sourced under an auditable annotation protocol. Where possible, have annotations reviewed independently and record inter-rater agreement.

Report at minimum:

- Dice overlap;
- intersection over union;
- pointing-game accuracy or localisation error;
- method and threshold sensitivity;
- saliency randomisation or parameter-randomisation sanity checks;
- results by tumour class and model variant.

The current three-case visual review remains valid qualitative evidence but cannot be pooled with mask-based metrics.

## 5. Release and audit artefacts

Each completed evaluation release should include:

- source commit and checkpoint SHA256 hashes;
- dependency lock and hardware/software environment;
- split and sample manifests;
- per-image prediction files;
- evaluation command lines;
- tables and figures generated directly from released data;
- a changelog identifying which article claims were updated.

## Publication gate

A row in the article's Evidence Readiness table may move from a completion gate to a verified result only when the corresponding machine-readable artefacts and reproduction instructions are publicly available.
