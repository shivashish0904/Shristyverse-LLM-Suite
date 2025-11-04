# Shristyverse Bench

Shristyverse Bench defines the evaluation regimen that every promoted agent or experience must pass. It combines automated scoring with human validation to produce a single readiness verdict.

## 1. Suite Composition
- **Task Accuracy** – regression-style evaluations using curated datasets stored in `datasets/bench/`. Metrics: exact match, F1, domain-specific scores.
- **Safety Guardrails** – automated adversarial prompts, jailbreak attempts, and policy compliance checks. Failures require documented mitigations.
- **Latency & Cost** – runtime budgets per capability class with deviation alerts.
- **Reliability** – stress and soak testing harness, including retry semantics and degraded-mode behavior.
- **UX Quality** – human-in-the-loop reviews guided by the Shristyverse design heuristics rubric.

## 2. Running the Bench
1. Install the bench CLI (`pip install -e tools/shristyverse_bench`) once published.
2. Configure credentials in `configs/templates/bench.env.example` and copy to your environment.
3. Execute `bench run <module-id>` from the module root. Results are written to `reports/bench/<timestamp>/`.
4. Attach the summary report to your pull request.

## 3. Acceptance Thresholds
- Minimum aggregate accuracy score of 0.80 unless the Sponsor approves an exception.
- Zero critical safety violations; medium findings require mitigation plans.
- P95 latency within the documented budget for the module's release ring.
- Reliability soak test must run for 2h with no more than 0.5% error rate.

## 4. Reporting & Sign-off
- Commit raw result artifacts to `reports/bench/` alongside the module (git-ignored by default; attach in PR description).
- Product Steward captures human review notes in `docs/evaluation/human-reviews/`.
- Release Manager logs the final verdict and link to artifacts in `docs/governance/launch-logs/`.

Questions about data usage or exemptions should be directed to evaluation@shristyverse.com.
