# First stop-condition pilot

Prepared 2026-11-19, before the first trial. Protocol author: Codex GPT-6 (directed by Esa-Pekka Pälvimäki).

## Decision rule

The pilot asks whether phase tests save work while preserving valid results under the same hard deadline.
Reject a tested policy if B stops even one paired run whose A partner reaches full credit.
For independent live samples, that count measures a paired disagreement. It cannot identify the stopped worker's counterfactual.
Report every pair. No population margin or significance claim follows from zero observed losses.

## Arms and units

A stops on voluntary exit, a hard deadline, or an operator request. B also stops on a failed phase check.
A evaluates the same checks in shadow. Both arms spend the same five model turns at most.
Each call asks for one JSON action. Final success never asks the controller to stop either arm.
The independent grader recomputes correct results from source rows. It scores current state after every accepted action.
Report first full credit and final full credit. Save the latest verified prefix and best verified prefix separately.
Only controller receipt before the monotonic cutoff earns credit. An incomplete line earns no credit.
Run elapsed time includes worker startup and confirmation of local process exit.
Post-success time includes idle time and the model's decision to finish. Count later published actions separately.
The experiment does not meter energy, inference tokens, or remote service work after cancellation.

## Design

Two tasks require a correct intermediate object and a correct final object. Both phases have equal weight.
Each proponent writes typed JSON equality tests and sets two absolute deadlines before work starts.
A finite interpreter accepts data only. A separate grader computes the true answers independently.
The model sees the task and interface before planning. It never receives the independent oracle or fixtures.
Hold each accepted plan fixed across arms and repetitions for that task, model, and dataset.
Validate on positive and negative fixtures. Allow one repair for a rejected proposal. Keep both versions.
Treat unavailable plans as scheduled runs without a start. Report access failures separately.
Store the plan outside the action interface. Check the locked file digest before and after every run.
The scripted workers use tests written by the orchestrator. Live workers use tests written by their own model.
The scripted worker cannot write files. The live model can submit JSON actions only.
A trusted local relay launches each model client within its own filesystem and process sandbox.
Only the local relay accesses client credentials. The model receives synthetic task text.
Each arm starts with empty state and a new working directory. No cross-arm conversation or feedback exists.

## Prespecified schedule

Random seed 20261119 shuffles pair order and the first arm. The second repetition reverses that arm order.
Each scripted task has two repeats under each of three behaviors. This gives 12 pairs and 24 runs.
Normal work reaches full credit before both checks. It stays active past both scheduled check times.
Repeated work publishes the correct intermediate answer until cancellation. Slow work publishes its correct final answer after the phase deadline.
The scripted hard limit is 2.30 seconds. The two checks occur at 0.65 and 1.25 seconds.
Four extra operator trials cover a blocked read and an owned child in both arms.
One extra B trial injects a verifier exception. Confirm a paused OS state, then dispose of the worker.
Local process-group disappearance is the exit criterion. Record all observed member identities and exit latencies.
Each of two live models receives both tasks twice under natural service timing. This gives eight pairs and 16 runs.
Use the same 90-second hard deadline, five-turn limit, low reasoning effort, and no model tools in both arms.
Two live pairs can run concurrently. Control arms and treatment arms run sequentially within each pair.
Model output and service latency can differ between two calls. No fixed inference seed exists.
Use deterministic scripted pairs for exact timing counterexamples. Inspect each stopped live pair individually.
A short trial cannot measure production shutdown behavior, hostile descendants, or sustained autonomy.

## Amendments from the independent review

GLM 5.3 Flash returned a conditional GO before the first experiment.
Both arms share one frozen plan. After first full credit, phase checks become inactive in both arms.
A missing artifact fails its due check. The controller records its absence separately from unchanged or incorrect content.
The fixture suite includes unchanged inputs, empty arrays, empty objects, stubs, and the initial state.
Count a phase-stop loss only when A reaches full credit and B never does before its phase stop.
Keep other paired disagreements separate.
The primary comparison uses paired elapsed differences across all timed runs. Report failures and completions separately.
Treat elapsed savings from lost completions as a cost to interpret, never as verified waste removal.
Use repeated submissions and time after full credit as separate measures of waste.
Include plan costs separately because both arms share the same plan.
The scheduled script offsets and actual publication times show where each stopped trace ends.
