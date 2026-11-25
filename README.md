# CognitiveTrack

A responsive longitudinal cognitive assessment prototype with synthetic demonstration data. Open `dist/index.html`, or run `node preview.cjs` and visit `http://127.0.0.1:8765`.

## Features

Patient directory with search and status filtering; chronological assessment entry; individual baseline comparison; interactive domain trajectories; reaction-time monitoring; explainable alerts with persisted review notes; patient history; HTML patient reports, CSV assessments and JSON backup/restore. All data is stored in browser localStorage on the current origin. Local-preview data and hosted-site data are separate.

## Interpretation

The earliest assessment is the baseline. Composite is the rounded unweighted mean of four 0–100 domain scores. Relative score deterioration is `(baseline - latest) / baseline * 100`; reaction-time deterioration is `(latest - baseline) / baseline * 100`. Zero score baselines are excluded from relative comparisons. The default illustrative review threshold is 10%, and monitor status begins at half the configured threshold. Reviews do not alter the underlying score classification. New assessment data invalidates a patient's old review acknowledgments and recomputes their trajectory.

This is a demonstrator, not a clinically validated diagnostic or reliable-change model. It does not include age-adjusted norms, psychometric measurement error, practice effects, authentication within the app, a patient database, cross-device synchronization or clinical-system integrations. Use synthetic data only. Real deployment for patient care requires a validated assessment protocol and analysis method, secure backend, access controls, audit trail, retention policy and appropriate clinical review. The sample timeline ends in November 2026.

## Verification

`node --check dist/app.js` checks syntax. `node check.cjs` verifies baseline logic, domain and reaction changes, classification, review state, backup validation, zero baseline handling, escaping and date range filtering.
