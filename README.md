# SARSA with Tile Coding on Mountain Car

This repository contains an implementation of the **SARSA (State-Action-Reward-State-Action)** algorithm using **tile coding** for function approximation in the **Mountain Car** control task. The agent learns to reach the top of the mountain by building momentum, despite starting with insufficient power.

## Overview

The Mountain Car problem is a benchmark reinforcement learning environment that features a continuous state space (position, velocity). This project uses tile coding—a coarse coding method from Sutton & Barto—to discretize the state space and approximate the value function using linear function approximation.

---

## Algorithms

- **SARSA (On-policy TD Control)**:
  - Updates action-value estimates using current and next actions.
  - Uses ε-greedy policy for exploration.

- **Tile Coding**:
  - Multiple overlapping tilings to discretize continuous input space.
  - Allows generalization while preserving fine distinctions between states.

---

## Project Structure

```
├── agent.py # SarsaAgent implementation using tile coding
├── tiles3.py # Tile coding utility (Tiles3 implementation)
├── mountaincar_env.py # Mountain Car environment (compatible with RL-Glue)
├── rl_glue.py # RL-Glue interface
├── utils.py # argmax with random tie-breaking
├── experiments.ipynb # Jupyter notebook with all experimental results
├── requirements.txt
└── README.md # This file
```
---

## Running the Code

## Experimental Comparisons
We compared three tile coding configurations with 512 total features:

Configuration	Avg Steps/Episode	Notes
```
2 Tilings × 16×16	| Slower convergence	| Sparse generalization
4 Tilings × 32×32	| Best performance	  | Dense features with better coverage
8 Tilings × 8×8	  | Good performance	  | Balanced generalization and learning
```

The best performing setup was 32×32 tiles with 4 tilings using α = 0.5 / num_tilings.
