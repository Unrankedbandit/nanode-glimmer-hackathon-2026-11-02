# Claude handoff: create the hackathon presentation/PDF

Use this repository as the source package for a chart-led hackathon presentation and, if requested, a PDF. The co-hacker is preparing the slides. PDF work in the originating chat was explicitly stopped; do the document work here in Claude instead.

## Main instruction

Explain the goal, high-level method, evaluation dimensions, measured outcomes and limitations with **more charts and less text**. Show the positive offline results alongside the failed end-to-end mesh attempts. Do not imply that production-quality meshes or a first-versus-fifth visual improvement were demonstrated.

This package is self-contained and sanitized. It deliberately omits the proprietary modeling workflow, original demonstration traces, source assets, production code, credentials, account information and private model/checkpoint identifiers. Do not try to reconstruct or invent them.

## What we set out to do

Specialize an open model for a better 3D modeling workflow using supervised fine-tuning on recorded expert demonstrations. Compare the original model with its LoRA on accuracy, efficiency, latency, cost and actual exported mesh quality. The intended pitch was measurable base-to-better improvement, including visible 3D output.

## What actually happened

1. Curated observed next-action examples and split by identified asset-family groups before extracting/evaluating examples. Groups are disjoint across splits; perceptual/source independence was not certified.
2. Ran one SFT epoch on **Muse Glimmer 30B**, using a **rank-8 LoRA**. The base weights were not fully fine-tuned.
3. Froze the final checkpoint and held-out evaluation configuration before opening the final test.
4. Completed a paired offline comparison on the same **100 held-out cases / 12 families**: 100 base requests and 100 LoRA requests. All 200 returned.
5. Tried the same complex original asset with both models. The initial campaign failed to export meshes. A training/live input-format mismatch was discovered afterward; its causal role is unproven.
6. Ran a separately labelled corrected five-version campaign. It also exported **zero meshes from both arms**. No iteration 1 or iteration 5 exists to view. No further model runs were started after these outcomes.

## Exact numbers for slides

| Dimension | Base | LoRA | Correct interpretation |
|---|---:|---:|---|
| Valid action format | 61/100 | 95/100 | +34 percentage points; output/schema compliance |
| Expected next-tool agreement | 41/100 | 93/100 | +52 percentage points; next-action proxy |
| Exact recorded-action match | 1/100 | 4/100 | Small, uncertain gain; family-bootstrap interval crosses zero |
| Median response latency | 3.8177 s | 2.3222 s | 39.2% lower observed client latency |
| p95 response latency | 19.3340 s | 9.8927 s | 48.8% lower observed client latency |
| Input tokens, held-out arm | 1,366,866 | 1,366,866 | Identical input workload |
| Output tokens, held-out arm | 28,204 | 14,736 | 47.8% less output; relevant to latency |
| Uncached list-rate estimate | $2.8167 | $2.7510 | Estimated inference cost, not billed spend |
| Corrected mesh versions exported | 0 | 0 | No visual mesh-quality comparison achieved |

**Training:** 597 examples / 28 families; validation 50 / 6; test 100 / 12. Only 16 of the 50 validation examples were used for a base-only preliminary probe. Training: 38 optimizer steps, one epoch, rank 8, alpha 32, learning rate 0.0001, batch size 16. Wall time **897.749 seconds = 14m58s**, including setup, checkpoint saving and promotion; earlier data/runtime preparation excluded. **10,616,154 training tokens** processed, approximately **11,825 training tokens/s** end to end. **113,373 assistant target/loss tokens** are a different quantity from all training tokens.

**Evaluation configuration:** temperature 0, 1,024 output-token cap per held-out request, concurrency 4. Client wall latency includes request overhead, prefill, waiting and output; TTFT and pure decode speed were not measured. Both arms use the same inputs. Cases within a family are correlated; do not treat them as 100 independent assets. The 12 families are identified lineage groups, not a certification of perceptual/source independence.

**Budget:** $50 hard cumulative cap; $40 operating ceiling plus $10 reserve inside the $50. Conservative reservations total **$35.64763696**. That is reserved allowance, not spend. The last available account billing snapshot, at 15:09 PST, showed $0 recorded cost but may lag. Final invoice spend is unknown. Glimmer SFT had a free-training promotion; do not claim all inference was free. GLM training was investigated but not launched; the user put it on hold unless more credits become available.

## Actual mesh test and visual dimensions

Original requested asset: **armored tortoise courier robot**, dimensions **0.60 m X width, 0.90 m Y length, 0.65 m Z height**, front toward -Y, centered at X=Y=0, grounded at Z=0, overall bounds including appendages, tolerance 5%.

Five feature domains: organic anatomy; beveled hard-surface armor; integrated machinery; exact raised lettering **NANODE 01**; fabric saddle pouch. The precommitted semantic rubric adds coherent overall courier silhouette: six axes scored 0, 1 or 2, maximum 12. **Every semantic score is UNASSESSED**, because there is no mesh. See `docs/HERO_BRIEF.md` and `data/semantic_rubric.csv`.

Physical evaluation was planned separately: exact-export reimport, dimensions, ground/centering, geometry defects, triangle range and export structure. Fixed front/rear/side/top cameras were planned. Iteration means an actual distinct source-and-mesh revision, not a tool call or training step.

| Campaign | Base outcome | LoRA outcome |
|---|---|---|
| Initial complex attempt | 2 recorded actions, then an unclassified action/controller failure | 20 actions, step limit |
| Corrected five-version attempt | 30 actions, iteration target not met | 21 actions, context limit |
| Exported meshes in either campaign | 0 | 0 |

The initial unclassified failure's exact cause is unknown. The corrected campaign changed the live input format and refinement instructions/allowance; keep it separate from the original campaign. Four attempted runs are not a statistical population estimate of model reliability.

## Assets to use

Start with `data/chart_index.json`. Every chart has PNG and SVG versions:

1. `01_results_dashboard`: headline action metrics, latency, output volume and list-rate cost estimates.
2. `02_latency_distribution`: full client-latency distributions.
3. `03_stage_pass_rates`: exploratory stage breakdown; small denominators must stay visible.
4. `04_tokens_vs_latency`: output volume versus full response latency; association, not causal attribution.
5. `05_training_loss`: observed per-batch training loss, not held-out validation loss.
6. `06_dataset_splits`: example and identified-family counts.
7. `07_missing_mesh_gallery`: honest missing base/LoRA iteration 1/5 matrix. It is not a rendered asset.
8. `08_semantic_rubric`: planned visual assessment dimensions, all unassessed.

The 200 anonymous case rows preserve pair/family grouping for additional charts. Their original prompts, answers and identifying asset names are absent. `data/RESULTS.json` and `docs/DATA_DICTIONARY.md` define the measurements. Use `SLIDE_OUTLINE.md` as a layout starting point.

## Claims to avoid

- Do not call 95% action-format compliance a 95% modeling success rate.
- Do not claim higher visual mesh quality, production-ready meshes or completed iteration-5 improvements.
- Do not invent placeholder 3D renders or present trusted control fixtures / old assets as model outputs.
- Do not call shorter observed responses an intrinsic model decoding-speed gain.
- Do not call per-batch training loss a validation or generalization curve.
- Do not equate a budget reservation, list-rate estimate or delayed billing snapshot with final spend.
- Do not imply GLM was trained, the model was deployed to the application, or EC2 generated these outputs.

## Suggested ending

"The LoRA improved structured next-action behavior on the held-out continuation set. The full 3D task still failed. The next milestone is actual exported meshes evaluated visually and physically under the same budgeted comparison."

Keep this limitation visible. Prefer a clear, honest result over a stronger unsupported pitch.
