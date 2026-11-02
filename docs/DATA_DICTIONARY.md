# Public data dictionary

All exports are aggregate or anonymous numeric measurements. There are no prompts, responses, actions, code, traces, source asset IDs, account identifiers, internal endpoints, credentials or filesystem paths.

| File | Contents |
|---|---|
| `RESULTS.json` | Reviewed counts, recipe, metrics, scope, failed mesh attempts, dimensions, budget and limitations |
| `paired_cases.csv` / `.json` | 200 rows: 100 identical held-out cases × two arms, anonymous case001–case100 and family F01–F12 |
| `stage_results.csv` | Per-arm counts for seven high-level stages; denominator is assigned cases |
| `training_steps.csv` | 38 batches: completed examples, training/target token counts and loss |
| `dataset_splits.csv` | 597/50/100 action examples and 28/6/12 disjoint asset families |
| `mesh_attempts.csv` | All four actual end-to-end attempts, including failures and zero exports |
| `semantic_rubric.csv` | Six criteria, planned 0–2 scale, every score UNASSESSED |
| `chart_index.json` | Captions and PNG/SVG paths for eight slide-ready figures |

`format_valid` requires strict JSON and the required action schema. `expected_tool_match` compares tool choice to the recorded teacher. `arguments_exact` compares arguments exactly. `exact_teacher_action` requires exact full teacher action agreement. These are offline proxies, not semantic geometry or execution validation. `response_clean` is the sampler's clean-termination marker, not a quality score. `request_failed` retains failures in the assigned-case denominator.

`client_latency_s` is observed full response latency, not TTFT or intrinsic decode speed. Concurrency was 4. Every held-out call returned a response. Lower generated output volume may explain some latency improvement.

Training loss is provider batch loss sum divided by that batch's assistant target-token count. Batches contain different training cases; this is not a held-out loss curve. Training tokens include full contexts; assistant loss tokens identify supervised output positions.

Costs use three separate labels: list-rate estimates from completed token counts; conservative budget reservations; final invoice spend (unknown). The latest billing snapshot of $0 was delayed and is not proof of free inference. $35.64763696 is a reservation, not actual spend. Total authorization is $50, including a $10 reserve, with $40 operating ceiling.

Anonymous IDs are arbitrary within this package and contain no source IDs. Family groups preserve cluster structure for honest uncertainty calculations. Stage groups range from 3 to 24 paired cases; stage-specific percentages are exploratory. The teacher-action family-cluster interval includes no improvement.
