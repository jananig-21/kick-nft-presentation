# Kick + NFT: escaping the SPIQ flat spot in QAOA join-order optimization

Presentation material for the kick + NFT study on the new ("qaoa") QUBO formulation of the join-order problem.

**Start here: [KICK_NFT_COMPLETE_GUIDE.md](KICK_NFT_COMPLETE_GUIDE.md).** It explains every concept, run, file and figure, with the evidence behind each number, likely questions with answers, and a slide plan.

## Main results

| Problem, start | COBYLA from SPIQ | Kick 1.0 ×5 + NFT | Random ×5 + NFT (control) |
|---|---|---|---|
| P2, multi-start SPIQ point | 0.500 | **0.977** | 0.999 |
| P2, single-start SPIQ point | 0.000 | **0.973** | 0.975 |
| P4, single-start SPIQ point | 0.250 | **0.693** | 0.712 |
| 12 new problems (mean) | 0.365 | **0.904** | 0.963 |

Values are the mean probability of the optimal join plan. P2 and P4: 20 runs each, on seeds never used to choose the method. 12 new problems: 3 runs each.

- From the team's SPIQ starting point, all 10 optimizers tested stay where they start: the gradient there is zero and no single angle goes downhill.
- A random kick moves the circuit to sloped ground. NFT, whose model is exact for these circuits, is the only kicked optimizer that improves.
- The control experiment shows the gain comes from NFT plus several restarts chosen by measured energy ("multi-start NFT"), not from staying near SPIQ's angles.
- P5 (24 qubits) is interim: after 4 of 5 kicks, two of four runs reach 0.976 and 0.612, where every optimizer from SPIQ gives 0.00.

## Contents

| Path | What it is |
|---|---|
| `KICK_NFT_COMPLETE_GUIDE.md` | the complete explanation |
| `figures/` | 17 figures, numbered in presentation order |
| `data/` | results behind the figures: 12 new problems, control experiment, landscape measurements, figure numbers |
| `scripts/` | the code that produced the figures and measurements (for reference; it reads the full study's raw result files, which are not in this repository) |

All results come from noiseless statevector simulation with 10,240 shots per evaluation and QAOA depth 2.
