# Cliff Walking: SARSA vs. Q-Learning (On-Policy vs. Off-Policy)

This repository contains a comprehensive reinforcement learning study comparing the **SARSA** and **Q-Learning** algorithms using the OpenAI Gymnasium `CliffWalking-v0` environment.

## Project Overview
The "Cliff Walking" problem is a grid-world MDP where an agent must navigate from a start point (bottom-left) to a goal (bottom-right). The challenge lies in a "cliff" located between the start and goal; stepping on it results in a $-100$ reward and resets the agent to the starting position.

This project demonstrates the fundamental trade-off between **safety (SARSA)** and **optimality (Q-Learning)**.

## Tech Stack
* **Language:** Python
* **Environment:** [Gymnasium](https://gymnasium.farama.org/) (CliffWalking-v0)
* **Libraries:** NumPy, Matplotlib, Seaborn

## 📊 Experimental Setup
To ensure statistical significance, the algorithms were evaluated across **30 independent seeds** with the following hyperparameters:

| Hyperparameter | Value | Description |
| :--- | :--- | :--- |
| **Alpha ($\alpha$)** | 0.1 | Learning Rate |
| **Gamma ($\gamma$)** | 0.99 | Discount Factor |
| **Epsilon ($\epsilon$)** | 0.1 | Fixed Exploration Rate |
| **Episodes** | 500 | Training steps per seed |

## Key Results

### 1. Performance Comparison
The learning curves below display the sum of rewards per episode with a **95% Confidence Interval**.

* **SARSA** achieves a higher average reward (~ -17). As an **On-Policy** algorithm, it learns a path that accounts for its own $10\%$ exploration, choosing to stay away from the cliff.
* **Q-Learning** shows lower average rewards during training (~ -50 to -80). As an **Off-Policy** algorithm, it attempts to hug the cliff edge and frequently falls due to exploratory moves.

> **Note:** Place your `learning_curves.png` here.

### 2. Behavioral Analysis
The heatmaps and quiver plots confirm the divergent strategies:

* **SARSA (On-Policy):** Takes the "High Road." The policy arrows indicate the agent moves to the top-most rows to maintain a safety buffer from the cliff.
* **Q-Learning (Off-Policy):** Takes the "Cliff Edge." The policy learns the mathematically shortest 13-step path, ignoring the risk of accidental falls during the learning phase.

> **Note:** Place your `heatmap.png` and `policy_arrows.png` here.

## Core Insights
* **On-Policy (SARSA):** Learns the value of the policy it is actually following. It is "realistic" and prioritizes safety in environments where mistakes are costly.
* **Off-Policy (Q-Learning):** Learns the value of the *optimal* policy regardless of the agent's current behavior. It is "optimistic" and prioritizes absolute efficiency.

## How to Run
1.  Clone the repository:
    ```bash
    git clone [[[https://github.com/yourusername/cliff-walking-comparison.git](https://github.com/yourusername/cliff-walking-comparison.git](https://github.com/Barsha-bytes/SARSA-vs.-Q-Learning-Comparison/blob/main/README.md))](https://github.com/Barsha-bytes/SARSA-vs.-Q-Learning-Comparison/blob/main/README.md)
    ```
2.  Install dependencies:
    ```bash
    pip install gymnasium numpy matplotlib seaborn
    ```
3.  Open and run the Jupyter Notebook: `Kakshapati_Barsha_Lab4_Q-Learning.ipynb`
