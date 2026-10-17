# 06 — Retail Pricing Workbench

- **Application:** Pricing optimization
- **Portfolio project:** 06 of 15
- **Status:** Project brief defined. Dataset acquisition, ML, application and MLOps implementation have not started.

Part of [Tomas Ferrer's DS/ML portfolio](https://tomasferrer.com/).

## Project prompt

Build an end-to-end pricing optimization application that turns a published online dataset into a useful business decision. Implement the analysis, a trained machine learning component, a deployed application, its MLOps lifecycle, and a presentation. The learned model must influence the application's output. Begin with the dataset and adapt the scope to the evidence it actually contains.

### Business question and application

**Decision:** Which price maximizes expected contribution while meeting volume and price-change constraints?

**Application to build:** Change prices, demand conditions, and margins; compare the existing policy with candidate policies and inspect uncertainty.

Write a short project charter defining the user, current baseline, primary business KPI, guardrails, prediction time, and measurable success criteria before selecting a model. Explain which decision the model changes and the costs of incorrect decisions.

### Published dataset and raw data

Candidate: one category of [Dominick's scanner data](https://www.chicagobooth.edu/research/kilts/research-data/dominicks), with product/store/week units, prices, margins and promotion information. The provider's academic-use restriction requires resolving suitability before a public release; acquire another suitable published dataset if this source does not fit. Do not substitute invented training histories.

**Additional source/access notes:** Begin with one category and its UPC/movement files. Provider limits use to academic research: this selection remains conditional on suitability for the intended public portfolio. Logged price variation alone does not establish causal elasticity

Acquire a pinned source release into `data/raw/` and preserve the original bytes. Add a repeatable acquisition script and a manifest containing source URL, release/version, retrieval time, citation, terms, file sizes and SHA-256 checksums. Keep cleaned data in `data/interim/` and model-ready features/split assignments in `data/processed/`. Raw data stay out of Git unless redistribution is explicitly appropriate.

Audit labels, decision-time feature availability, duplicates, missingness, class balance, and temporal/group structure. If the candidate cannot support the task or intended use, find another suitable published dataset or narrow the question. Generated fixtures and economic scenarios are supplementary, clearly labeled artifacts.

### Machine learning component

**Required fitted component:** Trained demand-response model.

Fit a demand model to the published observations; compare regression with boosted trees, controlling for available store/product/calendar/promotion information. Use a bounded price search only within an explicit scenario and observed support. A causal pricing model requires justified treatment assignment or identification evidence, not price variation alone.

Produce a reproducible training command and save the fitted preprocessing, model and decision policy together where appropriate. Compare the learned approach with a simple baseline. Pretrained models may support the solution, but a pretrained API call or prompt alone does not fulfill the trained-component requirement.

### Evaluation and business impact

Out-of-time demand prediction, stability and support diagnostics. Report proposed-price economics as model-based scenarios; observed data do not reveal the optimal counterfactual price or establish realized profit uplift. Adapt the application if the audited data support predictive pricing analysis rather than causal optimization.

Separate development/model selection from final evaluation. Fit transformations on training data only and compare candidate and incumbent on the same evaluation protocol. Save metrics, uncertainty/robustness checks, and representative failure cases with code/data/model identifiers.

Connect model metrics to the business KPI, with explicit denominators, comparator, population and period. Distinguish measured service performance, offline evaluation, simulated policy value and outcomes that require a real rollout. Never invent company impact or actual stakeholder buy-in.

### MLOps requirements

**Project-specific operational evidence:** Release model and pricing constraints together; monitor price-support violations and simulated realized profit; test rollback to prior pricing policy.

Implement and demonstrate:

1. Data/schema validation and versioned acquisition, features, splits and configuration.
2. Reproducible training with MLflow experiment tracking and saved metrics/artifacts.
3. Model registration with code/data lineage, exact versions, candidate/incumbent comparison and promotion gates.
4. Production inference with validated inputs and meaningful tests, including consistency with the evaluated model.
5. Containerized deployment and GitHub Actions CI/CD, with a pinned model/image, health check, inference smoke test and release identifier.
6. Service telemetry and task-specific input/prediction/quality monitoring, alert criteria and a response runbook. Identify replayed quality reports separately when real outcome labels are unavailable.
7. A runnable data-refresh/retraining workflow that evaluates the replacement before promotion.
8. A demonstrated rollback to the previous model/application release and a successful post-rollback inference check.

Use the smallest architecture that completes this lifecycle. Select real-time or batch inference according to the decision; shared managed services are acceptable, while the repository remains independently reproducible.

### Communication and portfolio deliverables

- A readable README with setup, actual results, architecture, limitations, and links to the released demo/case study/slides.
- Purpose-specific notebooks and short executive summaries documenting important experiments and decisions.
- A stakeholder decision memo covering the recommendation, evidence, tradeoffs and proposed rollout.
- A personal ownership statement and dated operating record identifying what was implemented, actual service usage, model changes, and incident/rollback exercises.
- A working public demo with source-derived examples where permitted, plus screenshots or a short recorded fallback.
- An original 10–12 slide presentation: editable `presentation/slides.pptx`, reviewed `presentation/slides.pdf`, speaker notes and underlying figures. Include model evaluation, business implications, MLOps architecture and operational evidence.
- A case study prepared for `tomasferrer.com`, linking the repository, demo and presentation.

**Presentation story:** The distinction between predicting sales at historical prices and estimating the effect of changing a price.

## Completion checklist

- [ ] Published source acquired, checksum verified and provenance/profile recorded.
- [ ] Data audit, project charter, success criteria and evaluation protocol complete.
- [ ] Baseline and trained ML component evaluated; artifacts and failure analysis saved.
- [ ] Working application deployed with the exact evaluated model version.
- [ ] Tracking, registry, CI/CD, monitoring, retraining and rollback demonstrated.
- [ ] Stakeholder memo, ownership/operating record, case study and presentation complete.

## Current implementation

This repository currently contains the implementation brief and Git exclusions. The dataset links identify starting sources; acquisition and model results will be documented as implementation proceeds.
