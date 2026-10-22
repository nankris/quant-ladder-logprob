# Status: completed

GPU evaluation and the write-up are complete. The quant-ladder Colab session was stopped successfully; results/stop.txt is the shutdown record. Inference does not need to be rerun.

All five formats have 4,972 paired fresh rows. Frozen input and hypothesis checks pass (results/preregistration_audit.json). Retained recovery prefixes match their saved hashes. scripts/analyze.py reconstructs predictions from raw scores, checks IDs, excludes the original run's questions and the pilot questions, and computes the registered bootstrap intervals. Results and decision rules were not changed after seeing the confirmation data.

Overall DISPROVEN: Q4 -2.03 pp versus BF16, 95% CI [-2.80,-1.25], missing the fixed one-point non-inferiority margin. Q2 -40.99 pp, CI [-42.64,-39.36], passes the five-point degradation target. BF16 79.93%, Q4 77.90%, Q2 38.94%. Full-text sensitivity and post hoc split checks are disclosed.

Contents: README.md, writeup.md, blog.md (1,616 words), three 150-dpi charts, table.png, diagram.png plus editable Excalidraw JSON, and four terminal-style screenshots rendered from real files and program output. figures/colab_run.txt includes GPU, run, timing and shutdown excerpts. Conservative CU upper estimate 2.34 across two L4 allocations; exact first release time unknown. Account balance change 4.02 includes concurrent work and is not attributed entirely to this experiment. The initial 55-minute estimate is preserved; timing.json includes actual elapsed time and stage definitions.

Reproduction commands are in scripts/README.md. Running scripts/finalize.py again recomputes publication elapsed time, so avoid rerunning it unless you intend to update timing.
