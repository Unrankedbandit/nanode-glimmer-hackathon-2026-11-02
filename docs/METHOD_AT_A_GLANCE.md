# Method at a glance

1. Curate successful observed teacher continuations; supervise the visible next action, with complete observed context and no hidden reasoning.
2. Split disjointly by identified asset family: 597 training, 50 validation, 100 held-out test examples. Freeze checkpoint and evaluation setup before opening the test set. Perceptual/source independence has not been certified.
3. Train one epoch of rank-8 LoRA on Muse Glimmer 30B; record every training batch.
4. Compare the base and tuned models on the same 100 prompts, at temperature 0 and concurrency 4. Keep all cases and report both format/tool agreement and exact teacher action.
5. Separately attempt a fixed end-to-end hero task with identical tools, cameras and limits. Preserve failures and missing outputs.

The strongest measured improvement is action formatting and tool choice. Exact teacher actions remain rare; the clustered uncertainty interval includes zero. Real end-to-end modeling did not succeed in these attempts. Slides should present both findings together.
