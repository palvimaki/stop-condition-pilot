# Stop-condition pilot

Generated 2026-11-19T14:43:43+00:00 · Codex GPT-6 (directed by Esa-Pekka Pälvimäki)

Arm A used a hard deadline and operator cancellation.
Arm B also enforced the locked phase deadlines.
The independent grader awarded one point for each consecutive correct phase.
Two points at exit counted as a valid completion.

## Natural live model runs


| Worker | Scenario | Arm | Scheduled | Started | First success | Final score 0 / 1 / 2 | Confirmed exits | Elapsed sum (s) | Median first progress (s) | Median exit (s) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| gpt-6.1-sol | natural | A | 4 | 4 | 4 | 0 / 0 / 4 | 4 | 47.811 | 4.237 | 12.089 |
| gpt-6.1-sol | natural | B | 4 | 4 | 4 | 0 / 0 / 4 | 4 | 50.258 | 4.198 | 12.848 |
| gpt-6.1-terra | natural | A | 4 | 4 | 4 | 0 / 0 / 4 | 4 | 40.134 | 3.467 | 9.625 |
| gpt-6.1-terra | natural | B | 4 | 4 | 4 | 0 / 0 / 4 | 4 | 43.775 | 3.826 | 10.549 |


| Worker | Scenario | Arm | Stop triggers | Worker outcomes | Timed exits after success | Time after success (s) | Later output publications | Later model calls | Later completion notifications |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| gpt-6.1-sol | natural | A | natural_exit 4 | voluntary_done 4 | 4 | 15.805 | 0 | 4 | 4 |
| gpt-6.1-sol | natural | B | natural_exit 4 | voluntary_done 4 | 4 | 16.368 | 0 | 3 | 4 |
| gpt-6.1-terra | natural | A | natural_exit 4 | voluntary_done 4 | 4 | 12.264 | 0 | 4 | 4 |
| gpt-6.1-terra | natural | B | natural_exit 4 | voluntary_done 4 | 4 | 15.058 | 0 | 3 | 4 |

Positive time differences mean arm B ended sooner. Each difference uses measured elapsed time for both arms.

| Worker | Scenario | Pairs | Paired losses after phase stops | Outcome, pair count, and elapsed difference | All timed pairs, difference (s) |
| --- | --- | --- | --- | --- | --- |
| gpt-6.1-sol | natural | 4 | 0 | both complete 4 (-2.448 s) | -2.448 |
| gpt-6.1-terra | natural | 4 | 0 | both complete 4 (-3.641 s) | -3.641 |


| Worker | Scenario | Arm | Started | Runs reaching a check | Checks run | Failed checks | Service retries | Valid phase-two publications | Valid publications after phase-two deadline | Pending at exit | Correct pending values |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| gpt-6.1-sol | natural | A | 4 | 0 | 0 | 0 | 0 | 4 | 0 | 0 | 0 |
| gpt-6.1-sol | natural | B | 4 | 0 | 0 | 0 | 0 | 4 | 0 | 0 | 0 |
| gpt-6.1-terra | natural | A | 4 | 0 | 0 | 0 | 0 | 4 | 0 | 0 | 0 |
| gpt-6.1-terra | natural | B | 4 | 0 | 0 | 0 | 0 | 4 | 0 | 0 | 0 |

Arm A recorded check results without enforcing them.
The grader credited only published outputs.
The relay recorded retries while waiting to publish the same model response.
## Scripted controller tests


| Worker | Scenario | Arm | Scheduled | Started | First success | Final score 0 / 1 / 2 | Confirmed exits | Elapsed sum (s) | Median first progress (s) | Median exit (s) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| script | normal | A | 4 | 4 | 4 | 0 / 0 / 4 | 4 | 6.087 | 0.203 | 1.510 |
| script | normal | B | 4 | 4 | 4 | 0 / 0 / 4 | 4 | 6.118 | 0.207 | 1.516 |
| script | repeat | A | 4 | 4 | 0 | 0 / 4 / 0 | 4 | 9.331 | 0.207 | 2.329 |
| script | repeat | B | 4 | 4 | 0 | 0 / 4 / 0 | 4 | 5.141 | 0.210 | 1.281 |
| script | slow | A | 4 | 4 | 4 | 0 / 0 / 4 | 4 | 7.509 | 0.210 | 1.867 |
| script | slow | B | 4 | 4 | 0 | 0 / 4 / 0 | 4 | 5.132 | 0.208 | 1.280 |


| Worker | Scenario | Arm | Stop triggers | Worker outcomes | Timed exits after success | Time after success (s) | Later output publications | Later model calls | Later completion notifications |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| script | normal | A | natural_exit 4 | natural_exit 4 | 4 | 4.438 | 0 | 0 | 0 |
| script | normal | B | natural_exit 4 | natural_exit 4 | 4 | 4.466 | 0 | 0 | 0 |
| script | repeat | A | hard_deadline 4 | hard_deadline 4 | 0 | — | 0 | 0 | 0 |
| script | repeat | B | phase_failed 4 | phase_failed 4 | 0 | — | 0 | 0 | 0 |
| script | slow | A | natural_exit 4 | natural_exit 4 | 4 | 0.860 | 0 | 0 | 0 |
| script | slow | B | phase_failed 4 | phase_failed 4 | 0 | — | 0 | 0 | 0 |

Positive time differences mean arm B ended sooner. Each difference uses measured elapsed time for both arms.

| Worker | Scenario | Pairs | Paired losses after phase stops | Outcome, pair count, and elapsed difference | All timed pairs, difference (s) |
| --- | --- | --- | --- | --- | --- |
| script | normal | 4 | 0 | both complete 4 (-0.032 s) | -0.032 |
| script | repeat | 4 | 0 | neither complete 4 (4.190 s) | 4.190 |
| script | slow | 4 | 4 | A only 4 (2.377 s) | 2.377 |

## Additional live service stress trials

This group started after early natural runs finished.
The local relay imposed the publication delay.
Both arms used the original model plans and the token task.


| Worker | Scenario | Arm | Scheduled | Started | First success | Final score 0 / 1 / 2 | Confirmed exits | Elapsed sum (s) | Median first progress (s) | Median exit (s) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| gpt-6.1-sol | delayed | A | 2 | 2 | 2 | 0 / 0 / 2 | 2 | 143.539 | 3.936 | 71.762 |
| gpt-6.1-sol | delayed | B | 2 | 2 | 0 | 0 / 2 / 0 | 2 | 80.069 | 4.225 | 40.031 |
| gpt-6.1-sol | retry | A | 2 | 2 | 0 | 0 / 2 / 0 | 2 | 180.067 | 3.706 | 90.030 |
| gpt-6.1-sol | retry | B | 2 | 2 | 0 | 0 / 2 / 0 | 2 | 80.071 | 3.795 | 40.032 |
| gpt-6.1-terra | delayed | A | 2 | 2 | 2 | 0 / 0 / 2 | 2 | 142.285 | 3.289 | 71.134 |
| gpt-6.1-terra | delayed | B | 2 | 2 | 0 | 0 / 2 / 0 | 2 | 120.073 | 3.448 | 60.032 |
| gpt-6.1-terra | retry | A | 2 | 2 | 0 | 0 / 2 / 0 | 2 | 180.072 | 4.054 | 90.032 |
| gpt-6.1-terra | retry | B | 2 | 2 | 0 | 0 / 2 / 0 | 2 | 120.070 | 4.029 | 60.031 |


| Worker | Scenario | Arm | Stop triggers | Worker outcomes | Timed exits after success | Time after success (s) | Later output publications | Later model calls | Later completion notifications |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| gpt-6.1-sol | delayed | A | natural_exit 2 | voluntary_done 2 | 2 | 7.439 | 0 | 2 | 2 |
| gpt-6.1-sol | delayed | B | phase_failed 2 | phase_failed 2 | 0 | — | 0 | 0 | 0 |
| gpt-6.1-sol | retry | A | hard_deadline 2 | hard_deadline 2 | 0 | — | 0 | 0 | 0 |
| gpt-6.1-sol | retry | B | phase_failed 2 | phase_failed 2 | 0 | — | 0 | 0 | 0 |
| gpt-6.1-terra | delayed | A | natural_exit 2 | voluntary_done 2 | 2 | 6.163 | 0 | 2 | 2 |
| gpt-6.1-terra | delayed | B | phase_failed 2 | phase_failed 2 | 0 | — | 0 | 0 | 0 |
| gpt-6.1-terra | retry | A | hard_deadline 2 | hard_deadline 2 | 0 | — | 0 | 0 | 0 |
| gpt-6.1-terra | retry | B | phase_failed 2 | phase_failed 2 | 0 | — | 0 | 0 | 0 |

Positive time differences mean arm B ended sooner. Each difference uses measured elapsed time for both arms.

| Worker | Scenario | Pairs | Paired losses after phase stops | Outcome, pair count, and elapsed difference | All timed pairs, difference (s) |
| --- | --- | --- | --- | --- | --- |
| gpt-6.1-sol | delayed | 2 | 2 | A only 2 (63.470 s) | 63.470 |
| gpt-6.1-sol | retry | 2 | 0 | neither complete 2 (99.996 s) | 99.996 |
| gpt-6.1-terra | delayed | 2 | 2 | A only 2 (22.211 s) | 22.211 |
| gpt-6.1-terra | retry | 2 | 0 | neither complete 2 (60.002 s) | 60.002 |


| Worker | Scenario | Arm | Started | Runs reaching a check | Checks run | Failed checks | Service retries | Valid phase-two publications | Valid publications after phase-two deadline | Pending at exit | Correct pending values |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| gpt-6.1-sol | delayed | A | 2 | 2 | 4 | 2 | 25 | 2 | 2 | 0 | 0 |
| gpt-6.1-sol | delayed | B | 2 | 2 | 4 | 2 | 14 | 0 | 0 | 2 | 2 |
| gpt-6.1-sol | retry | A | 2 | 2 | 4 | 2 | 34 | 0 | 0 | 2 | 2 |
| gpt-6.1-sol | retry | B | 2 | 2 | 4 | 2 | 14 | 0 | 0 | 2 | 2 |
| gpt-6.1-terra | delayed | A | 2 | 2 | 4 | 2 | 26 | 2 | 2 | 0 | 0 |
| gpt-6.1-terra | delayed | B | 2 | 2 | 4 | 2 | 22 | 0 | 0 | 2 | 2 |
| gpt-6.1-terra | retry | A | 2 | 2 | 4 | 2 | 34 | 0 | 0 | 2 | 2 |
| gpt-6.1-terra | retry | B | 2 | 2 | 4 | 2 | 22 | 0 | 0 | 2 | 2 |

Arm A recorded check results without enforcing them.
The grader credited only published outputs.
The relay recorded retries while waiting to publish the same model response.
## Paired losses after phase stops


| Group | Pair | Baseline trace (s) | Phase-check trace (s) | Last verified output in B | Pending phase-two request in B |
| --- | --- | --- | --- | --- | --- |
| challenge | gpt-6.1-sol-tokens-delayed-1 | P1 score 1 at 3.644, P1 pass at 20.002, P2 fail at 40.002, P2 score 2 at 68.050 | P1 score 1 at 3.590, P1 pass at 20.003, P2 fail at 40.001 | {"1":["k","b","k","a","b","b","c"]} | {"a":1,"b":3,"c":1,"k":2}, oracle match True, 7 retries from 7.376 to 37.421 s |
| challenge | gpt-6.1-sol-tokens-delayed-2 | P1 score 1 at 4.229, P1 pass at 20.001, P2 fail at 40.000, P2 score 2 at 68.035 | P1 score 1 at 4.859, P1 pass at 20.001, P2 fail at 40.002 | {"1":["k","b","k","a","b","b","c"]} | {"a":1,"b":3,"c":1,"k":2}, oracle match True, 7 retries from 9.044 to 39.097 s |
| challenge | gpt-6.1-terra-tokens-delayed-1 | P1 score 1 at 3.437, P1 pass at 30.001, P2 fail at 60.001, P2 score 2 at 68.054 | P1 score 1 at 3.676, P1 pass at 30.002, P2 fail at 60.002 | {"1":["k","b","k","a","b","b","c"]} | {"a":1,"b":3,"c":1,"k":2}, oracle match True, 11 retries from 7.297 to 57.348 s |
| challenge | gpt-6.1-terra-tokens-delayed-2 | P1 score 1 at 3.142, P1 pass at 30.002, P2 fail at 60.001, P2 score 2 at 68.051 | P1 score 1 at 3.219, P1 pass at 30.001, P2 fail at 60.002 | {"1":["k","b","k","a","b","b","c"]} | {"a":1,"b":3,"c":1,"k":2}, oracle match True, 11 retries from 7.730 to 57.829 s |
| script | script-ledger-slow-1 | P1 score 1 at 0.209, P1 pass at 0.651, P2 fail at 1.252, P2 score 2 at 1.650 | P1 score 1 at 0.208, P1 pass at 0.652, P2 fail at 1.250 | {"1":{"amber":1,"blue":10,"red":4}} | No pending submission |
| script | script-ledger-slow-2 | P1 score 1 at 0.214, P1 pass at 0.652, P2 fail at 1.252, P2 score 2 at 1.654 | P1 score 1 at 0.209, P1 pass at 0.652, P2 fail at 1.251 | {"1":{"amber":1,"blue":10,"red":4}} | No pending submission |
| script | script-tokens-slow-1 | P1 score 1 at 0.209, P1 pass at 0.652, P2 fail at 1.251, P2 score 2 at 1.651 | P1 score 1 at 0.213, P1 pass at 0.652, P2 fail at 1.250 | {"1":["k","b","k","a","b","b","c"]} | No pending submission |
| script | script-tokens-slow-2 | P1 score 1 at 0.211, P1 pass at 0.652, P2 fail at 1.251, P2 score 2 at 1.653 | P1 score 1 at 0.192, P1 pass at 0.652, P2 fail at 1.252 | {"1":["k","b","k","a","b","b","c"]} | No pending submission |

Each row records a successful baseline and an incomplete phase-stop run.

12 scripted pairs had complete measurements.
Arm B stopped 4 runs whose baseline reached full credit.
This exceeds the prespecified limit of zero.

8 natural live pairs had complete measurements.
Arm B stopped 0 runs whose baseline reached full credit.
These observed pairs meet the zero-loss limit.

8 live service stress pairs had complete measurements.
Arm B stopped 4 runs whose baseline reached full credit.
This exceeds the prespecified limit of zero.

## Cancellation and verifier trials


| Scenario | Arm | Trigger | Signal | Processes at signal | Pause confirmed | Group exit confirmed | Stop to group exit (s) | Last verified output |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| blocked | A | operator_cancel | SIGTERM | 1 | None | True | 0.034 | {} |
| blocked | B | operator_cancel | SIGTERM | 1 | None | True | 0.035 | {} |
| child | A | operator_cancel | SIGTERM | 2 | None | True | 0.030 | {} |
| child | B | operator_cancel | SIGTERM | 2 | None | True | 0.049 | {} |
| fault | B | verifier_error | SIGSTOP, SIGTERM | 1, 1 | True | True | 0.043 | {"1":{"amber":1,"blue":10,"red":4}} |


## Phase test validation


| Group | Author | Task | Attempt | Status | Fixture passes | Proposed checks | Planner elapsed (s) | Failure detail |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| script | Codex orchestrator | ledger | attempt-1-1 | accepted | P1 13/13, P2 13/13 | P1 at 0.65 s equals {"amber":1,"blue":10,"red":4} / P2 at 1.25 s equals ["blue","red","amber"] | — | — |
| script | Codex orchestrator | tokens | attempt-1-1 | accepted | P1 13/13, P2 13/13 | P1 at 0.65 s equals ["k","b","k","a","b","b","c"] / P2 at 1.25 s equals {"a":1,"b":3,"c":1,"k":2} | — | — |
| live | gpt-6.1-sol | ledger | attempt-1-1 | accepted | P1 13/13, P2 13/13 | P1 at 30 s equals {"amber":1,"blue":10,"red":4} / P2 at 60 s equals ["blue","red","amber"] | 6.051 | — |
| live | gpt-6.1-sol | tokens | attempt-1-1 | accepted | P1 13/13, P2 13/13 | P1 at 20 s equals ["k","b","k","a","b","b","c"] / P2 at 40 s equals {"a":1,"b":3,"c":1,"k":2} | 4.577 | — |
| live | gpt-6.1-terra | ledger | attempt-1-1 | accepted | P1 13/13, P2 13/13 | P1 at 30 s equals {"amber":1,"blue":10,"red":4} / P2 at 60 s equals ["blue","red","amber"] | 4.560 | — |
| live | gpt-6.1-terra | tokens | attempt-1-1 | accepted | P1 13/13, P2 13/13 | P1 at 30 s equals ["k","b","k","a","b","b","c"] / P2 at 60 s equals {"a":1,"b":3,"c":1,"k":2} | 5.338 | — |


## Record checks

The available run records show no worker errors, missing runs, or inconsistent final scores.

The CSV contains each run's times, final score, and last verified output.
Each raw run record contains the ordered events and process observations.

## Limits

These tasks used fixed inputs and short, visible phases.
Fixture validation checked content. It did not establish safe deadlines.
A paired baseline shows what happened in another run.
Model calls can vary between runs with identical inputs.
Elapsed time includes service waits and exit confirmation.
Time after success includes any final call that returned a completion notification.
A completion notification ends work without publishing another phase output.
The stress trials measure imposed service waits. They cannot establish savings in model computation.
Exit checks cover local processes in the worker's process group.
This pilot cannot establish a production completion rate or production time savings.
