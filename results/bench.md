# ProofIntent-ML benchmark

Measured on this machine with the Python witness/proof simulator.
Times are the mean of 5 runs.

| Model | Mode | R1CS cost | Rows | Prove (ms) | Emulated prove (ms) | Verify (ms) | Peak mem (KB) | Verify OK |
|-------|------|-----------|------|------------|---------------------|-------------|---------------|-----------|
| mlp_small | baseline | 31 | 8 | 6.85 | 17.46 | 1.07 | 15.6 | True |
| mlp_small | optimized | 22 | 8 | 6.23 | 11.48 | 1.02 | 12.9 | True |
| mlp_large | baseline | 103 | 9 | 15.79 | 62.20 | 1.54 | 79.6 | True |
| mlp_large | optimized | 20 | 4 | 15.53 | 10.99 | 1.84 | 79.4 | True |

`Emulated prove` is a cost-proportional workload (field-multiply emulations per R1CS constraint) that illustrates how constraint reduction maps to proving effort on a real backend.

## Optimization effect

| Model | Baseline R1CS | Optimized R1CS | Removed | Reduction |
|-------|---------------|----------------|---------|-----------|
| mlp_small | 31 | 22 | 9 | 29.03% |
| mlp_large | 103 | 20 | 83 | 80.58% |
