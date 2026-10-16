# NeuraCare: Curated & Annotated DASS-42 Benchmark Dataset

[![ODI Open Data Certificate](https://certificates.theodi.org/datasets/6ad250fbb830b6ee9ba3991e/certificates/6ad251b9b830b6ee9ba39932/badge.png)](https://certificates.theodi.org/datasets/6ad250fbb830b6ee9ba3991e/certificates/6ad251b9b830b6ee9ba39932)

## Overview
This repository hosts a quality-filtered, normalized, and clinically annotated benchmark dataset (`N = 34,576`) derived from the Depression Anxiety Stress Scales (DASS-42). It was curated to train and evaluate multi-output machine learning classification pipelines for the **NeuraCare** mental health decision-support system.

## Curation & Pre-Processing Pipeline
Starting from raw OpenPsychometrics DASS-42 responses (`39,775` raw records, `172` columns), the following data engineering steps were executed:
1. **Attention & Validity Filtering:** Removed `5,199` invalid responses that failed the fake-word validity check (`VCL6 = 0`, `VCL9 = 0`, `VCL12 = 0`) or reported implausible demographic ages (filtered to `13 <= age <= 100`).
2. **Scale Standardization:** Shifted raw item responses (`Q1A`–`Q42A`) from `1–4` to the standard clinical DASS-42 Likert scale of `0–3` (`Q1`–`Q42`).
3. **Feature Selection & De-Identification:** Stripped `119` noisy reaction-time (`Q1E`–`Q42E`), item-order (`Q1I`–`Q42I`), network location, and sensitive metadata columns, retaining `42` psychometric items and `5` clean demographic indicators (`age`, `gender`, `education`, `urban`, `married`).
4. **Clinical Target Annotation:** Computed subscale sum totals (`Depression_Score`, `Anxiety_Score`, `Stress_Score`) and annotated 5-tier ordinal severity labels (`Normal`, `Mild`, `Moderate`, `Severe`, `Extremely Severe`) using official DASS-42 psychometric cutoffs.

## File Inventory
- `neuracare_dass42_curated.csv`: Cleaned dataset (`34,576` rows × `53` columns).
- `LICENSE`: Released under the MIT License.

## Attribution
Derived from public-domain psychometric survey data (OpenPsychometrics.org); cleaned, normalized, and annotated by the NeuraCare Project Team.
