
# Vehicle Sharing Network

Code for the paper “Tight Guarantees for Static Policies in Vehicle Sharing Networks” by Adam N. Elmachtoub and Jiaqi Shi.

Paper: https://arxiv.org/abs/2610.13089

## Numerical experiments

- `Table1.ipynb` reproduces Table 1: the minimum and average revenue ratios of the best offered-balanced static policy relative to the optimal static policy.
- The experiments use complete directed networks with `N(N-1)` arcs.
- The default settings are `N = 5, 10, 15, 20`, `C = 5, 20, 40`, and 100 random instances for both linear and exponential demand.

## Requirements

Python 3.12 with:

- NumPy
- SciPy
- CVXPY
- CLARABEL
- Matplotlib

Run the notebook from top to bottom. Generated CSV files and figures are saved under `output/optstatic_minimal/`.
