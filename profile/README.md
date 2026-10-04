# CeyNex

**Multi-agent decision intelligence for Sri Lanka's export economy, with every number traceable to its source.**

CeyNex answers questions about Sri Lanka's agriculture exports (tea, cinnamon, rubber, coconut) and apparel exports (knitted and woven garments) in plain English. Five specialised agents compute every figure from one integrated trade dataset and a knowledge graph. A language model only routes the question and writes the wording, and a guard removes any sentence that states a figure the agents did not supply. Each answer carries:

- an evidence panel showing the source and the exact query behind each figure;
- an explainable confidence score;
- for forecasts, an 80% prediction interval.

Live at <https://ceynex.cc> (sign-in required).

## Repositories

| Repository | What it holds |
|---|---|
| [ceynex-core](https://github.com/CeyNex-AI/ceynex-core) | Data pipeline, knowledge graph, five agents, LangGraph orchestrator, forecasting models, FastAPI backend, evaluation |
| [ceynex-web](https://github.com/CeyNex-AI/ceynex-web) | React front end: query workspace and chat, scenario workbench, admin console |
| [ceynex-contracts](https://github.com/CeyNex-AI/ceynex-contracts) | Frozen interfaces shared by every component, and the PostgreSQL and Neo4j schemas |
| [ceynex-infra](https://github.com/CeyNex-AI/ceynex-infra) | Docker Compose, nginx, Google Cloud setup, backups, monthly refresh, monitoring |
| [trade-data-pipeline](https://github.com/CeyNex-AI/trade-data-pipeline) | Builds the destination-market policy-document index in Qdrant |
| [data-analysis](https://github.com/CeyNex-AI/data-analysis) | One exploratory notebook per data source |

## At a glance

- **Data:** 13,132 trade observations from UN Comtrade, the Export Development Board, JAAF, FAOSTAT, the World Bank (Pink Sheet and exchange rates), and curated tea and cinnamon workbooks. Policy passages come from Sri Lanka's main export markets.
- **Stack:** Python, LangGraph, FastAPI, PostgreSQL, Neo4j, Qdrant, Redis, React and TypeScript, Docker, Google Compute Engine.
- **Models:** SARIMA, LightGBM and an equal-weight combination, chosen by rolling-origin back-testing. The best model reaches 5.2% MAPE on tea export value.
- **Evaluation:** 30 pre-registered questions, each asked five times, compared with the same LLM answering alone:

| Measure | LLM alone | CeyNex |
|---|---|---|
| Figures not in the dataset | 67.9% | 0.0% |
| Claims contradicted by the data | 15.7% | 0.4% |
| Unanswerable questions refused | 6.7% | 100% |

## Team

Group 07, Project P16, CS3501 Data Science and Engineering Project, University of Moratuwa.

| Member | Focus |
|---|---|
| Senindu Dinapura | Agriculture data and agent, evaluation, data provenance |
| Thisen Ekanayake | Core systems, orchestration, policy retrieval, infrastructure |
| Dhinanjaya Fernando | Apparel data and agent, forecasting, evaluation, front end, security |

Supervisor: Dr. Chathuranga Hettiarachchi.
