# Shristyverse LLM Suite Architecture

This overview explains how the repository evolves beyond a generic collection of demos into a cohesive Shristyverse platform. The intent is to make it obvious where to plug in new workstreams, automate evaluation, and deploy production-caliber experiences.

## 1. Platform Pillars

- **Foundations** – shared contracts, dataset loaders, and scaffolding that every app uses (`starter_ai_agents/`, `rag_tutorials/`).
- **Agency Layer** – high-agency orchestrators and planners that encode Shristyverse playbooks (`advanced_ai_agents/`, `mcp_ai_agents/`).
- **Interfaces** – experiments in user orchestration, multimodal IO, and voice (`voice_ai_agents/`, `advanced_llm_apps/`).

Each pillar publishes a `manifest.yaml` (planned in FY25 Q2) describing its publicly supported surfaces.

## 2. Workflow Flow

1. **Prototype** in `starter_ai_agents/` or `advanced_llm_apps/`.
2. **Instrument** the agent with the metrics harness in `advanced_ai_agents/metrics/` (coming soon).
3. **Package** the agent into an MCP-compliant service or a voice/multimodal interface.
4. **Promote** into production by linking it to internal governance pipelines (see `docs/governance/` roadmap).

## 3. Config Harmonization

- Shared secret templates live under `configs/templates/` (see `platform.env.example`, `bench.env.example`) and feed the monorepo secret manager.
- Module-specific `.env.example` files must be namespaced with `SHRISTYVERSE_` prefixes.

## 4. Release Rings

| Ring | Purpose | Branching |
| --- | --- | --- |
| Alpha | Internal prototypes | feature/\* |
| Beta | Partner pilots | release/\* |
| GA | Production-ready apps | main |

Promotion between rings requires passing the `Shristyverse Bench` evaluation suite (spec defined in `docs/evaluation/benchmarks.md`, forthcoming).

## 5. Next Steps

- Stand up the shared observability library under `platform/observability/` and populate `docs/observability/` with runbooks.
- Publish the Shristyverse Bench harness alongside standardized datasets and adopt the `docs/evaluation/templates/bench_report.md` for evidence.
- Automate MCP adapter testing through GitHub Actions (workflow spec under review).

For roadmap updates or architectural decisions, submit a proposal PR targeting this document. Reach out to architecture@shristyverse.com for clarifications.
