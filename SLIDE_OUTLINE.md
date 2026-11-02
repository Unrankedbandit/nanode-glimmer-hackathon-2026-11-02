# Chart-first slide sequence

| Slide | Main point | Visual | Text budget |
|---|---|---|---|
| 1. Goal | Specialize an open model for a better 3D workflow | Simple base -> SFT -> measured comparison diagram | One sentence |
| 2. Data and recipe | 597 / 50 / 100 examples, disjoint families, one rank-8 LoRA epoch | `06_dataset_splits` plus small recipe labels | Three labels |
| 3. Observed training | 38 steps in 14m58s | `05_training_loss` | Two caveats: different batches; not validation loss |
| 4. Held-out action results | Format 61% -> 95%, expected tool 41% -> 93% | `01_results_dashboard` | One scope sentence: action proxies, not meshes |
| 5. Speed and efficiency | Median 3.82s -> 2.32s, with less output | `02_latency_distribution`, `04_tokens_vs_latency` | One qualification: no pure decode-speed measurement |
| 6. Coverage | Gains vary by workflow stage | `03_stage_pass_rates` | Keep every stage's sample count visible |
| 7. The intended visual evaluation | Armor, organics, machinery, lettering, fabric, silhouette | `08_semantic_rubric`, asset dimensions | All semantic scores unassessed |
| 8. What did not work | Neither arm exported a mesh | `07_missing_mesh_gallery`, four-run outcome table | No iteration 1/5 or visual-quality gain exists |
| 9. Budget and next milestone | $50 cap, $35.65 reserved; actual invoice unknown | Reserved / estimated / billed labels, separate | Next milestone: real meshes with visual and physical evaluation |

Use SVGs when possible. Keep units, denominators, failure counts and missing outputs visible. No invented asset images.
