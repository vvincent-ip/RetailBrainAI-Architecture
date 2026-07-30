# Claude Code Guide — SDK-032

```text
Implement SDK-032 as a production forecasting platform, not a notebook, demo or single-model POC.

Read the agentic AI/forecasting architecture and stable SDK-009, SDK-011 and SDK-030 contracts. Define forecast definition, dataset/feature snapshot, model, training run, backtest, forecast product, interval, hierarchy, scenario, override, approval, actual and accuracy contracts.

Implement data eligibility and leakage controls, reproducible feature/training/inference pipelines, baseline plus candidate models, time-series cross-validation, champion/challenger selection, intermittent-demand support, hierarchy/temporal reconciliation, prediction intervals, scenario generation, publication approval, overrides, immutable lineage, actual ingestion, accuracy/bias/drift monitoring, retraining triggers, rollback and deterministic fallback.

Add production orchestration/serving and model-registry adapters, scalable batch processing, isolation, idempotency, recovery, load/soak and failure tests, accuracy benchmarks by segment/horizon, security, cost controls, dashboards/alerts, customer deployment/configuration, model governance, retraining, override, backup/restore and incident runbooks.

Do not let forecasts directly execute business actions. Do not declare success based only on aggregate accuracy or one sample dataset. Completion requires reproducibility and customer-place operational acceptance.
```
