# Reproduction and recovery

Use the frozen `results/items.json`, `pilot.json`, `manifest.json` and the committed README. Do not resample based on observed results. The sample-size amendment was committed as a8c729c before confirmation. The first protocol was committed before the pilot (see git history).

GPU execution used a detached worker on the experiment's Colab L4. `launch.py` installs/starts `worker.py` under `/content/quant-ladder`. `prepare.py` verifies model file hashes and prepares data. `evaluate.py FORMAT confirm` appends and flushes scored rows, skips completed IDs, and locks each output format. `auxiliary.py` is a second serial queue on that same GPU, never another session. Dependencies and GPU evidence are in results/packages.txt and figures/colab_run.txt. The first VM was lost; `recovery_control.py` describes the replacement controller. Retained row hashes are checked during analysis.

The existing results need no GPU to analyze. From the repository root (needs numpy, matplotlib and Pillow):

```sh
python scripts/audit_prereg.py
python scripts/analyze.py > results/analysis_output.txt
python scripts/finalize.py > results/finalization_output.txt
python scripts/report.py
python scripts/screenshots.py > results/screenshots_output.txt
python scripts/verify.py
```

`finalize.py` recalculates publication elapsed time, so running it later changes timing.json, not the predictions or verdict. It requires saved successful shutdown evidence. `monitor.py` is the local checkpoint downloader and stops only quant-ladder on completion/error or the conservative budget threshold. Remote GPU processes do not depend on it staying alive. If the local monitor dies, restart it without starting new inference while the job still runs.

Excalidraw source is figures/diagram.excalidraw. The diagram PNG was already rendered before recovery and inspected after recovery; the diagram can be re-exported from the JSON with any Excalidraw export tool. Screenshot source excerpts are program-generated directly from the archived writeup and final statistics, via scripts/termshot.py.
