# Heart Failure Readmission Risk Scoring System

**RWJBarnabas Health** | Clinical AI | Multimodal Risk Prediction | Built with Snowflake

---

An interactive clinical decision-support application that guides the development of a **multimodal heart failure 30-day readmission risk prediction model** for RWJBarnabas Health's 12 acute care hospitals across New Jersey.

| | |
|---|---|
| **Risk Factors** | 91 across 7 data categories |
| **Hospitals** | 12 RWJBH acute care facilities |
| **Evidence Base** | 500+ PubMed studies, 50+ curated citations |
| **Target AUC** | 0.75 - 0.82 (vs. 0.59-0.65 for structured-only models) |

## The Problem

Current HF readmission models (LACE, HOSPITAL score) rely on structured EHR data alone and plateau at **AUC 0.59-0.65**. Our approach combines seven data modalities to push performance toward **AUC 0.75-0.82**:

| Data Category | Example Factors | Impact |
|---|---|---|
| **Structured Clinical** | Ejection fraction, BNP, eGFR, hemoglobin, sodium | Baseline |
| **NLP / Unstructured** | Discharge summary sentiment, med adherence mentions, functional status | +5-9% AUC |
| **Social Determinants** | ADI, food insecurity, housing instability, insurance gaps | +2-4% AUC |
| **Behavioral** | Appointment no-shows, smoking status, substance use, PHQ-9 | +1-3% AUC |
| **Imaging / Diagnostics** | Echo reports (AI-parsed), chest X-ray congestion, ECG rhythm | +1-2% AUC |
| **Temporal / Trajectory** | Weight trend (7-day), BNP trajectory, prior HF admissions (12-month) | +2-4% AUC |
| **Post-Discharge** | 7-day follow-up, RPM/telehealth compliance, med reconciliation | +1-3% AUC |

## Application Sections

1. **System Overview** - Hospital cards for all 12 RWJBH facilities with CMS star ratings and readmission rates. Evidence case for multimodal modeling.
2. **Quality Benchmarks** - RWJBH vs. national leaders (Cleveland Clinic, NYU, Mt. Sinai). NJ state context, national trend timeline 2010-2025, mortality benchmarks (NQF #0229).
3. **Research & Evidence Base** - Seven research tabs: RWJBH Publications, Foundational Evidence, NLP/Unstructured, SDoH, Emerging Factors, Code Sets & Data Standards, State & Policy Evidence.
4. **RWJBH Heart Stories** - Patient stories and heart care content from across the RWJBH system.
5. **State Case Studies** - Six state-level case studies: Massachusetts (15.3%), NJ/RWJBH (~14.7%), Idaho (13.3%), West Virginia, Nevada, and lessons for RWJBH.
6. **Risk Factor Review** - Interactive cardiologist review interface with include/exclude toggles, drag-and-drop reordering, editable strength ratings, evidence hyperlinks, category filtering, and custom factor addition.
7. **Review & Model Creation** - Phase tracking, review status controls with timestamped audit log, CSV/summary export, and the 5-phase development roadmap.

## Development Roadmap

| Phase | Description | Status |
|---|---|---|
| **1** | Cardiologist Review of Risk Factors | Active |
| **2** | Snowflake Data Element Scan & Gap Analysis | Upcoming |
| **3** | Model Create, Train & Test Cycles (Snowpark ML + Model Registry) | Upcoming |
| **4** | Model Deployment for Inference (Snowpark Container Services) | Upcoming |
| **5** | Epic Hyperspace Integration (CDS Hooks + External Functions) | Upcoming |

## Applicability Beyond HF Readmission

The framework is reusable across any clinical risk prediction use case:

- **Sepsis early warning** - vitals trajectory + NLP + labs
- **Surgical complication prediction** - imaging + structured + temporal patterns
- **ED return visits / observation stays** - behavioral + SDoH + post-discharge signals
- **Mortality risk stratification** - already benchmarked in the app
- **Length-of-stay prediction** - same factor categories, different outcome variable
- **CHF progression modeling** - longitudinal EF trajectory + BNP trends + med adherence

## Technology Stack

- **Snowflake** - Centralized data warehouse (Epic Clarity/Caboodle, claims, ADT, SDoH)
- **Snowpark ML** - Model training with cross-validation and fairness evaluation
- **Snowflake Model Registry** - Model versioning and governance
- **Snowpark Container Services** - Real-time inference at admission and discharge
- **Cortex AI** - NLP extraction from clinical notes
- **Epic Hyperspace + CDS Hooks** - Clinical workflow integration

## Usage

Open `rwjbh_hf_readmission.html` in any modern browser. No installation, server, or credentials required.

Review status and audit log are persisted in browser local storage. Closing and reopening restores your progress. Clear local storage to reset.

## Files

| File | Description |
|---|---|
| `rwjbh_hf_readmission.html` | Main application |
| `RWJBH_HF_App_Summary.html` | Email-ready team summary |

---

*RWJBarnabas Health - Clinical Decision Support - Internal Use - Built with Snowflake*
