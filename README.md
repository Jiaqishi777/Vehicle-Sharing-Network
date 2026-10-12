# Tight Guarantees for Static Policies in Vehicle Sharing Networks

This repository contains the code used to reproduce **Table 1** in [*Tight Guarantees for Static Policies in Vehicle Sharing Networks*](https://arxiv.org/abs/2610.13089).

## Table 1

**Revenue ratio of the best balanced static policy relative to the optimal static policy**

`Table1.ipynb` computes the optimal static revenue from formulation (12) and the best balanced static revenue using line search of $\Delta$ over the flow relaxation (7).

## Numerical experiments

We consider a complete directed network with $N(N-1)$ arcs for each $N$.

We consider linear demand,

$$p^{ij}(\lambda)=b^{ij}-a^{ij}\lambda,$$

and exponential demand,

$$p^{ij}(\lambda)=a^{ij}\log\!\left(\frac{b^{ij}}{a^{ij}\lambda}\right),$$

with $\Lambda^{ij}=b^{ij}/a^{ij}$.

We use $N\in\{5,10,15,20\}$ and $C\in\{5,20,40\}$ and generate 100 independent instances for each pair $(N,C)$ and each demand family. Independently across arcs, we draw $a^{ij}$ uniformly from $[0.1,5]$, $b^{ij}$ uniformly from $[0.5,10]$, and $\mu^{ij}$ uniformly from $[0.2,5]$.

For each instance, the notebook computes the optimal static revenue and the best balanced static revenue. The default experiment contains 2,400 instances.

## Requirements

- Python 3.12
- NumPy
- SciPy
- CVXPY
- CLARABEL
- Jupyter Notebook or JupyterLab

Install the required packages with

```bash
python -m pip install numpy scipy cvxpy clarabel jupyter
```

The saved results were produced with Python 3.12.13, NumPy 2.5.1, SciPy 1.18.0, CVXPY 1.9.2, and CLARABEL 0.11.1.

## Reproducing the results

1. Open `Table1.ipynb`.
2. Select **Restart Kernel and Run All**.
3. Leave `NUM_INSTANCES = 100` to reproduce the full experiment.

For a quick execution check, set `NUM_INSTANCES = 1`. To reproduce the reported results, use the default value `NUM_INSTANCES = 100` and run all cells from a restarted kernel.

## Results

Table 1 reports the best balanced static revenue as a percentage of the optimal static revenue.

| $N$ | $C$ | Linear Min. | Linear Avg. | Exponential Min. | Exponential Avg. |
|---:|---:|---:|---:|---:|---:|
| 5 | 5 | 80.66% | 94.73% | 89.30% | 97.04% |
| 5 | 20 | 92.02% | 97.90% | 96.97% | 99.08% |
| 5 | 40 | 95.77% | 98.68% | 98.90% | 99.55% |
| 10 | 5 | 71.08% | 94.29% | 94.70% | 97.76% |
| 10 | 20 | 92.82% | 97.43% | 97.40% | 99.13% |
| 10 | 40 | 94.94% | 98.30% | 99.02% | 99.54% |
| 15 | 5 | 80.15% | 94.75% | 95.62% | 97.99% |
| 15 | 20 | 88.10% | 96.59% | 98.04% | 99.12% |
| 15 | 40 | 95.59% | 98.08% | 99.19% | 99.56% |
| 20 | 5 | 82.55% | 94.80% | 96.49% | 98.25% |
| 20 | 20 | 89.35% | 96.76% | 98.75% | 99.26% |
| 20 | 40 | 95.19% | 97.93% | 98.99% | 99.54% |

The average ratio ranges from 94.29% to 99.56%, while the smallest observed ratio is 71.08%. For every fixed $N$ and both demand families, the minimum and average ratios increase with $C$. The ratios are also consistently higher under exponential demand than under linear demand.

## Output files

After the experiment finishes, the notebook writes the following files to `output/table1/`:

- `instance_results.csv`: results and numerical diagnostics for every instance;
- `summary.csv`: the minimum and average ratios reported in Table 1.

## Code

- `Table1.ipynb`: the numerical methods, instance generation, experiment, and output.
