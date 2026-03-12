# 🧬 Sports League Scheduling Optimization using Genetic Algorithms

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)

**Developed by:** João Luís Marques, Gustavo Gomes, Rodrigo Luis

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Methodology: The Genetic Algorithm](#methodology-the-genetic-algorithm)
3. [Repository Structure](#repository-structure)
4. [Key Results & Insights](#key-results--insights)
5. [How to Run](#how-to-run)

---

## Project Overview

This project was developed for the **Computational Intelligence for Optimization (CIFO)** course at **NOVA IMS**. The goal was to solve a highly complex combinatorial optimization problem: **Sports League Scheduling**.

Creating a fair and efficient league schedule requires satisfying numerous hard constraints — including team availability, minimizing consecutive home/away games, and balancing travel distances. To tackle this, we designed, tuned, and implemented a custom **Genetic Algorithm (GA) from scratch in Python**, capable of navigating the massive search space and finding near-optimal schedules efficiently.

---

## Methodology: The Genetic Algorithm

Our solution explores the search space using evolutionary heuristics. We rigorously tested multiple configurations across factors and levels, evaluating them based on **fitness convergence**, **structural diversity**, and **CPU efficiency**.

### Optimal Configuration

After extensive batch testing, the following GA architecture yielded the best results, reaching the optimal fitness in **>90% of seeds within 65–70 generations**:

| Component | Configuration | Rationale |
|---|---|---|
| **Population Size** | `40` | Same average quality as size 80, saving ~45% CPU time |
| **Selection** | Truncation (40%) | Efficient selection pressure without diversity loss |
| **Crossover** | Team-mask crossover | Preserves team-level schedule structure |
| **Mutation** | Swap + Kempe chain (`Pₘ = 0.10`) | Maintains excellent structural diversity |
| **Elitism** | `2` | Ensures the best schedules are never lost across generations |

---

## Repository Structure
```
├── CIFO_GROUP_H.ipynb    # Main notebook — Genetic Algorithm implementation
├── GROUP_H_REPORT.pdf    # Full report: methodology, parameter tuning, and results
└── Test instances/       # Dataset folder with league constraints and input scenarios
```

---

## Key Results & Insights

- **Convergence:** The tuned algorithm reliably reaches the best fitness score, typically stabilising around generation 65.
- **Mutation Synergy:** Combining simple swap mutations with Kempe chain mutations effectively prevents premature convergence to local optima.
- **Efficiency:** Strict parameter tuning — reducing population size and using truncation selection — drastically reduced computational overhead while maintaining top-tier solution quality.

---

## How to Run

1. Clone this repository:
```bash
   git clone <repository-url>
   cd <repository-folder>
```

2. Open the notebook in Jupyter Notebook, JupyterLab, or Google Colab:
```bash
   jupyter notebook CIFO_GROUP_H.ipynb
```

3. Ensure the `Test instances/` folder is in the same directory as the notebook.

4. Run the cells sequentially to initialise the population, apply the genetic operators, and start the evolutionary loop.
