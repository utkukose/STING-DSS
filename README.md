<div align="center">

<img src="https://img.shields.io/badge/TÜBİTAK_1001-123E383-1F4E79?style=for-the-badge" />
<img src="https://img.shields.io/badge/Role-Principal_Investigator-17748A?style=for-the-badge" />
<img src="https://img.shields.io/badge/License-Apache_2.0-green?style=for-the-badge" />

<br /><br />

# STING DSS

### Drug Repositioning and Synthetic Patient Treatment Decision Support System
### *for Childhood Acute Lymphoblastic Leukemia*

**My role:** Principal Investigator · System architect · Lead developer

[**Project Repository**](https://github.com/tubitaksting) · [**Live System**](http://37.148.208.183:8091) · [**Publications & Data**](https://sting.sdu.edu.tr) · [**My GitHub**](https://github.com/utkukose)

</div>

---

## About this repository

This repository provides an overview of the STING DSS research project. The full source code, deployment configuration, and technical documentation are maintained at the official project repository:

> **[github.com/tubitaksting](https://github.com/tubitaksting)**

For publications, datasets, and citable outputs, visit the project website:

> **[sting.sdu.edu.tr](https://sting.sdu.edu.tr)**

---

## What is STING DSS?

STING DSS is a full-stack clinical research platform I designed and built as part of TÜBİTAK 1001 Project No. 123E383 (2023–2026) at Süleyman Demirel University. It integrates five AI/ML methodologies into a single, sequential pipeline for pediatric ALL research — from raw drug–protein interaction data all the way to population-level synthetic patient cohort analysis.

The system is deployed as a production-ready, bilingual (TR/EN) web application accessible to the research team and collaborators worldwide.

---

## My contributions

**Research leadership**
- Conceived and directed the overall research programme
- Designed the five-layer methodological architecture connecting drug repositioning, ODE simulation, genetic algorithm optimisation, GNN digital twin prediction, and GAN synthetic patient generation
- Developed the unified 5-class risk stratification ontology harmonising NCI, COG, BFM, and SJCRH criteria

**System development**
- Architected and implemented the full-stack platform: FastAPI backend, React/Vite frontend, Docker Compose infrastructure
- Designed and implemented `TenDrugALLModel` — a 48-dimensional ODE system modelling 10 drugs across 4 treatment phases with RK45 adaptive solver
- Implemented GNN v2 (GCNConv×2, h=256) digital twin achieving median R² = 0.991 across 8 treatment outcome targets
- Designed the clean-schema CTGAN architecture eliminating label leakage (GAN-label concordance 0.41%), with post-hoc clinical enrichment pipeline
- Implemented all four XAI methods: SHAP KernelExplainer, Permutation Importance, Counterfactual search, and GEMEX

**Open-source library**
- Developed and published **[GEMEX v1.2.2](https://pypi.org/project/gemex/)** — a Riemannian manifold-based explainability library (`pip install gemex`) used within the STING pipeline for geodesic sensitivity field analysis

**Production deployment**
- Deployed the system to a Natro VPS with Nginx reverse proxy, JWT authentication, bcrypt password hashing, slowapi rate limiting, and hardened API configuration
- Built bilingual Admin Panel with user management, activity logging, and TÜBİTAK research survey integration

---

## Pipeline overview

```
Tab 1  Bi-LSTM Drug Repositioning      314,531 ligand–protein pairs (DrugBank · ChEMBL · PubChem · KIBA)
  │                                    Copanlisib: −207.11 kcal/mol · Novobiocin: HSP90 inhibitor
  ▼
Tab 2  Patient & Treatment Setup       10 drugs · 4 phases · BSA · TPMT · Vitamin D · lifestyle factors
  │
  ▼
Tab 3  ODE PK/PD Simulation           TenDrugALLModel · 48-dim state · RK45 · 250 days
  │                                    Sensitivity: Vitamin D 48.1% impact on WBC minimum
  ▼
Tab 4  GA Dose Optimisation           BRR d8: 99.64% · EOI MRD: 3.3×10⁻⁵ · DNR: 149.2 mg/m²
  │
  ▼
Tab 5  GNN Digital Twin + XAI         Median R²: 0.991 · SHAP · Permutation · GEMEX · Counterfactual
  │
  ▼
Tab 6  Synthetic Cohort (GAN)         200 patients · 5-class risk · COP+NOV: Lt→0.000 · WBC +17.5%
```

---

## Selected technical highlights

| Component | Detail |
|-----------|--------|
| ODE engine | `TenDrugALLModel` — 48-dim state vector, 10 drugs, 4 phases, RK45 solver |
| GA optimisation | Population 80 · Generations 200 · 4 simultaneous clinical objectives |
| GNN architecture | GCNConv×2 (h=256, dropout=0.2) · heterogeneous patient graph · k=3 lag |
| CTGAN design | Clean-schema (30 static features) · post-hoc MRD/risk/PI/prognosis pipeline |
| XAI — GEMEX | Geodesic Sensitivity Field · Riemannian manifold · κ = 0.5612 (example patient) |
| Privacy validation | MIA AUC = 0.530 (≈ random) · clinical violation rate = 0% |
| Deployment | Docker Compose · Nginx · Redis · Celery · JWT · bcrypt · slowapi |
| Languages | Bilingual TR/EN · light/dark theme · session management |

---

## Tech stack

```
Backend          FastAPI · Python 3.10+ · PyTorch · SciPy (RK45) · SDV/CTGAN · SHAP · GEMEX v1.2.2
Frontend         React 18 · Vite · Recharts · D3.js · Tailwind CSS
Infrastructure   Docker Compose · Nginx · Redis · Celery · JWT · bcrypt · slowapi
```

---

## Project team

| Name | Role |
|------|------|
| **Prof. Dr. Utku Köse** *(me)* · [utkukose.com](https://utkukose.com) · [ORCID](https://orcid.org/0000-0002-9652-6415) | Principal Investigator / Developer — SDU / University of North Dakota / VelTech / Universidad Panamericana |
| Prof. Dr. Gözde Özkan Tükel | Researcher / Developer — Süleyman Demirel University |
| Dr. İlhan Uysal | Researcher / Developer — Burdur Mehmet Akif Ersoy University |
| Lect. Osman Ceylan | Researcher / Developer — Isparta Applied Sciences University |
| Lect. Emine Betül Sürücü | Researcher / Developer — Süleyman Demirel University |

---

## Funding

Supported by the **Scientific and Technological Research Council of Türkiye (TÜBİTAK)**, 1001 Programme, **Project No: 123E383** (2023–2026), Süleyman Demirel University.

---

## Links

| | |
|--|--|
| Full source code & docs | [github.com/tubitaksting](https://github.com/tubitaksting) |
| Live system | [37.148.208.183:8091](http://37.148.208.183:8091) |
| Publications, datasets & citations | [sting.sdu.edu.tr](https://sting.sdu.edu.tr) |
| GEMEX library (PyPI) | [pypi.org/project/gemex](https://pypi.org/project/gemex/) |
| My GitHub profile | [github.com/utkukose](https://github.com/utkukose) |
| My website | [utkukose.com](https://utkukose.com) |
| ORCID | [0000-0002-9652-6415](https://orcid.org/0000-0002-9652-6415) |

---

## Disclaimer

STING DSS is a research prototype. Outputs have not been validated against real clinical data and must not be used for clinical decision-making. Apache 2.0 License.

---

<div align="center">

*This repository is maintained by Prof. Dr. Utku Köse as part of the STING project.*
*For the full codebase, visit [github.com/tubitaksting](https://github.com/tubitaksting).*

</div>
