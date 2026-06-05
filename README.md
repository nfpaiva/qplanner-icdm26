# Code — Diagnosing ML-Driven Queue Systems in Production

**Paper:** *Diagnosing ML-Driven Queue Systems in Production*  
**Conference:** ICDM 2026 Applied Track  
**Authors:** Nuno Paiva, João Varela, João Gama

---

## Notebooks

| Notebook | Corresponds to | Paper section |
|---|---|---|
| `nb2-simulator-calibration.ipynb` | Discrete-event simulator build + θ_OCC calibration sweep + validation | §6 Simulator Calibration |
| `nb3-scenario-evaluation.ipynb` | 23-scenario evaluation — parameter sweeps (L0–L2) + structural separation (L3) | §7 Experiments (Table 1) |

---

## Dependencies

```
python >= 3.10
pandas
numpy
scipy          # Hungarian algorithm via linear_sum_assignment
matplotlib
seaborn
```

Install with:
```bash
pip install pandas numpy scipy matplotlib seaborn
```

---

## Data

Production telemetry is proprietary and cannot be shared.  
To run the notebooks with your own data, replace the **Data Loading Stub** cells
with a loader that produces two DataFrames matching the schemas described in each
notebook:

- **`df_ops`** — operational results (one row per call)
- **`df_scores`** — call-operator pairings / brains scores (one row per scored pair per tick)

Column schemas are documented in the markdown cells at the top of each notebook.

---

## Reproducing Table 1

1. Provide data matching the schemas above
2. Run `nb2-simulator-calibration.ipynb` end-to-end to obtain `theta_OCC* = 1.27`
3. Run `nb3-scenario-evaluation.ipynb` with 5 seeds × 21 days to reproduce Table 1

Expected runtime: < 2 hours per scenario on a standard workstation (32 GB RAM).
