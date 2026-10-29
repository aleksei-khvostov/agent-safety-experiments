# Agent Safety Experiments

Historical prototypes for studying execution-state reporting and oversight. This repository mixes deterministic fixture demonstrations with separately saved model-response pilots. Results must be read by evidence type.

## What the bridge results establish

| Historical script/artifact | Cases | Recorded “planner_accuracy” | Recorded divergence | Evidence type |
|---|---:|---:|---:|---|
| bridge_emergent_eval.py | 12 | 75% | 25% | Deterministic fixture/scorer output; no model inference |
| bridge_mixed_state_eval.py | 20 | 30% | 70% | Deterministic fixture/scorer output; no model inference |

In both scripts, `planner_report(worker_output)` returns its input unchanged. Substring rules then normalize that text. The first script counts every `AMBIGUOUS` prediction as divergence, even when the authored actual label is also `AMBIGUOUS`; the mixed-state script uses label inequality alone. These rates follow from the fixtures and different scoring rules. They do not measure LLM planner accuracy or establish emergent model behavior. Historical filenames and result fields remain unchanged for provenance.

The bridge watchdog compares the same actual/reported labels used to define divergence. Its 100% detection and 0% false-positive rates are agreement by construction, not independent semantic oversight validation.

## Other evidence

- [Tool-description pilot](experiments/tool_description_safety/README.md): saved model outputs, simulated tools, small sample. The broad and guarded tools differ in runtime behavior as well as description; this does not isolate a description-only causal effect.
- [Delegation baseline](experiments/delegation_safety/README.md): deterministic keyword policy on eight authored tasks; no LLM planner.
- [Reporting consistency](experiments/reporting_consistency/README.md): model-backed reporting scripts and saved responses, with lexical scoring and separately labeled historical rescoring. No new runs are implied.
- [Watchdog prototypes](experiments/watchdog_evaluation/README.md): rule-based “semantic” normalization on authored cases; that name does not indicate an LLM judge.
- [Bridge prototype](experiments/bridge_planner_worker_watchdog/README.md): independent authored actual-state labels and deterministic report/scoring paths.

## Phase 2 provenance

Findings 005–007 belong to the controlled Phase 2 prototype preserved in [multi-agent-safety-sim](https://github.com/aleksei-khvostov/multi-agent-safety-sim/tree/main/research/phase2_oversight_signal). They describe those fixtures and rules, not general watchdog effectiveness.

- [Findings](https://github.com/aleksei-khvostov/multi-agent-safety-sim/blob/main/research/phase2_oversight_signal/docs/FINDINGS.md)
- [Oversight signal experiment](https://github.com/aleksei-khvostov/multi-agent-safety-sim/blob/main/research/phase2_oversight_signal/docs/OVERSIGHT_SIGNAL_EXPERIMENT.md)
- [Trace ablation](https://github.com/aleksei-khvostov/multi-agent-safety-sim/blob/main/research/phase2_oversight_signal/docs/TRACE_ABLATION_EXPERIMENT.md)
- [Trace without final state](https://github.com/aleksei-khvostov/multi-agent-safety-sim/blob/main/research/phase2_oversight_signal/docs/TRACE_WITHOUT_FINAL_STATE_EXPERIMENT.md)

## Reproducibility and limits

See the preserved [Research Summary](RESEARCH_SUMMARY.md) for the historical sequence; the evidence qualifications in this README govern interpretation of its claims. Bridge scripts write result files when executed; reproduce only in a disposable copy. Some other scripts invoke hosted models at import or execution time. This repository has no committed dependency specification, automated test suite, or CI workflow. No general model-safety or architecture ranking follows from these prototypes.

The packaged simulator contains later work. Its [current research state](https://github.com/aleksei-khvostov/multi-agent-safety-sim/blob/main/docs/CURRENT_RESEARCH_STATE.md) governs its own authorization boundaries; historical plans here do not authorize new model experiments.
