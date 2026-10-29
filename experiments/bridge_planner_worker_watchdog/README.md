# Planner → Worker → Watchdog Bridge Experiment

This experiment is a bridge between the small controlled experiments in this repository and the larger `multi-agent-safety-sim` project.

The scripts demonstrate state/report separation and deterministic normalization on authored fixtures. The “emergent” filenames are historical: in `bridge_emergent_eval.py` and `bridge_mixed_state_eval.py`, the planner returns fixture text unchanged. `bridge_eval.py` uses a scripted planner. No LLM inference occurs in these bridge scripts. See the [repository README](../../README.md) for scoring differences and the circular watchdog comparison.

See `BRIDGE_CRITERIA.md` for the pre-registered design.
