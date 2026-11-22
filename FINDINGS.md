# Can phase checks stop wasted work safely?

Generated 2026-11-19T14:43:43+00:00 · Codex GPT-6 (directed by Esa-Pekka Pälvimäki)

The tested rules failed the zero-loss criterion.
Both models finished ordinary tasks before the first check.
Under delayed publication, the same rules stopped workers whose baseline partners finished before 90 seconds.

## Outcomes

A used the hard deadline and operator cancellation. B also enforced the frozen phase checks.
Elapsed time sums individual runs. The final grader required both correct outputs.
A loss means B stopped for a phase failure before success and A reached full credit.

| Condition | Pairs | Valid completions A / B | Total seconds A / B | Paired losses |
|---|---:|---:|---:|---:|
| Natural model work | 8 | 8 / 8 | 87.9 / 94.0 | 0 |
| Model with repeated writes | 4 | 0 / 0 | 360.1 / 200.1 | 0 |
| Model with delayed write | 4 | 4 / 0 | 285.8 / 200.1 | 4 |
| Scripted normal work | 4 | 4 / 4 | 6.1 / 6.1 | 0 |
| Scripted repeated work | 4 | 0 / 0 | 9.3 / 5.1 | 0 |
| Scripted slow work | 4 | 4 / 0 | 7.5 / 5.1 | 4 |

Natural runs reached 0 active phase checks.
After first success, workers used 28.1 seconds in A and 31.4 seconds in B.
They submitted 0 further outputs. The final model call let the worker declare completion.

In 4 of 4 stopped delayed runs, the waiting submission already contained the correct answer.
Only published answers earned credit. The trace also recorded each pending answer.
Repeated and delayed writes used a controlled local service. Its retries required no additional model calls.
The faster exits under permanent delay saved waiting time. The pilot did not measure inference cost.

## Controller and tests

The pilot recorded 61 runs. All 61 local process groups exited.
Stop triggers were 8 hard_deadline, 32 natural_exit, 4 operator_cancel, 16 phase_failed, 1 verifier_error.
All 4 operator cancellations ended the blocked work. Exit confirmation took 30–49 milliseconds.
Both child-process trials included the parent and child in the cancellation signal.
The injected verifier exception paused the worker. The controller confirmed the pause before cleanup.

The models proposed eight phase tests. The orchestrator supplied four scripted tests.
All twelve tests passed 156 fixture checks combined. No proposal needed repair.
The four live proposals took 20.5 seconds summed across calls.
Fixtures checked output content. They could not validate the proposed timing under service delays.

## Interpretation

The natural comparison showed no opportunity for phase checks to save work.
The service trials show how a correct result can wait for publication.
At the phase deadline, that run can look identical to a run that will never publish.
Two models, two fixed tasks, and shared service timing limit generalization.
Even 8 independent pairs with zero losses would permit a 31.2% one-sided 95% upper bound.
These repeated tasks do not supply that independence.
This pilot establishes local process exit. Remote inference shutdown and production-agent effects remain unmeasured.

An independent model (GLM 5.3 Flash) reviewed the protocol before the first trial; its amendments were incorporated prior to execution.
The live service stress group was specified after early natural runs and before any stress outcome.

The detailed report includes individual paired losses and all proposed deadlines. [Detailed report](results/REPORT.md)
The CSV contains timings, grades, stop triggers, and retained outputs for each run. [Per-run measurements](results/run-summary.csv)
Raw event traces and local host execution scripts are omitted from this report-only archive.
