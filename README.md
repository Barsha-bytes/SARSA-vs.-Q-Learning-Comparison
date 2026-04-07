# Cliff Walking: SARSA vs. Q-Learning Analysis

This repository explores the fundamental differences between **On-Policy** and **Off-Policy** reinforcement learning using the `CliffWalking-v0` environment. 

## Project Overview
The goal is to navigate an agent from a starting point to a goal while avoiding a "cliff" that incurs a -100 penalty. This project demonstrates why **SARSA** prioritizes safety while **Q-Learning** prioritizes mathematical optimality.

## 🛠️ Tech Stack
* **Language:** Python
* **Libraries:** Gymnasium, NumPy, Matplotlib, Seaborn
* **Algorithms:** SARSA (On-Policy), Q-Learning (Off-Policy)

## Experimental Results

### 1. Performance Training Curves
The following plot represents the sum of rewards per episode, averaged over **30 independent seeds** with a 95% confidence interval. 

![Learning Curves](images/1output.png)

* **SARSA** converges to a higher total reward because it avoids the cliff.
* **Q-Learning** has lower average rewards during training because its exploratory moves often lead to "falling" off the edge.

### 2. Value Function Heatmaps
These heatmaps show the "Value" ($V(s)$) of each state. 

| SARSA (Safe Knowledge) | Q-Learning (Optimal Knowledge) |
| :---: | :---: |
| ![SARSA Heatmap](images/Heatmap_Sarsa.png) | ![Q-Learning Heatmap](images/Q_Learning_Heatmap.png) |

* **SARSA** values the states near the cliff much lower (red/yellow), reflecting its cautious nature.
* **Q-Learning** maintains higher values near the edge because it assumes perfect future play.

### 3. Learned Policies (Quiver Plots)
The policy arrows show the final strategy developed by each agent.

**SARSA Strategy (The Safe High Road):**
![SARSA Policy](images/Learned_Policy.png)

**Q-Learning Strategy (The Risky Shortest Path):**
![Q-Learning Policy](images/Learn_Policy_Q_learning.png)

## Core Insights
| Feature | SARSA | Q-Learning |
| :--- | :--- | :--- |
| **Update Type** | On-Policy | Off-Policy |
| **Strategy** | Cautious / Safe | Optimal / Risky |
| **Path Taken** | Long way around | Along the cliff edge |
| **Best Use Case** | Physical robots / High-risk | Simulations / Low-risk |

