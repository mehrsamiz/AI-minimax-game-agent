# Hand of the King — Adversarial AI Agent

An intelligent game-playing agent built for the *Hand of the King* turn-based strategy board game. This project was developed as the **Final Project for the Artificial Intelligence course (Fall 2024)**. It focuses on classical adversarial search techniques, implementing a deep tree-search algorithm optimized via alpha-beta pruning and dynamic heuristic evaluation to establish a rigorous algorithmic baseline.

---

## Project Architecture & Codebase Attribution
The foundational game loop, graphical user interface (Pygame), and baseline asset pipeline were designed by the course instructional team and can be reviewed in the upstream source repository: []. 

The algorithmic core, strategic decision-making engine, and heuristic systems were engineered independently:
*   **`my_agent.py`**: Contains the complete implementation of the adversarial search architecture, game-state evaluation mathematical modeling, and tree-pruning systems.
*   `main.py` / `random_agent.py` / `assets/` / `utils/`: Base execution framework and game components provided as structural infrastructure.

---

## Key Engineering & Algorithmic Features

### 1. Minimax with Alpha-Beta Pruning
The agent navigates the complex, competitive state space of the game by building a multi-turn lookahead tree using the Minimax algorithm. To ensure real-time execution under strict turn-time constraints, **Alpha-Beta Pruning** was implemented to eliminate sub-optimal paths early, yielding a significant decrease in computation time and effective branching factor.

### 2. Dynamic Search Depth Adaptation
Rather than utilizing a rigid depth limit, the agent scales its lookahead horizon based on real-time computational complexity and structural stages of the game:
*   **Early Game:** Focused on localized, highly branching initial moves (Depth 2).
*   **Mid-Game:** Expanded lookahead as the board state clarifies (Depth 3).
*   **Late Game:** Deep endgame calculation to secure definitive board configurations and winning paths (Depth 4+).

### 3. Stage-Dependent Multi-Factored Heuristics
Because a static evaluation function cannot capture the shifting tactical dynamics of a board game, the state evaluation matrix scales dynamically across three distinct game phases:
*   **Early Game Matrix:** Prioritizes card hoarding, flexibility, and maximization of potential future move transitions.
*   **Mid-Game Matrix:** Transitions toward securing majority banner control and optimizing strategic house capture.
*   **Endgame Matrix:** Shifts aggressively toward opponent blocking, disrupting enemy point potential, and securing absolute card majorities.

---

## Installation & Requirements

### Prerequisites
* Python 3.8 or higher
* Pygame

### Setup
1. Clone this repository:
   ```bash
   git clone [https://github.com/mehrsamiz/AI-minimax-game-agent](https://github.com/mehrsamiz/AI-minimax-game-agent)


## Running the Game

To evaluate the performance of the Minimax agent against the stochastic baseline framework, execute main.py from the root directory using the following command:

```Bash
python main.py --player1 "my_agent" --player2 "random_agent"
```

## Evaluation Framework

The agent's performance was evaluated against a stochastic baseline engine (random_agent.py) to quantify decision-making capability under varying initialization constraints. The custom Minimax agent consistently achieves an optimal win-rate convergence, demonstrating high tactical stability across a diverse spectrum of randomized initial board configurations.

## Pipeline Horizon: Phase 2 (Learning & Optimization Paradigms)
>  **Project Migration Notice:** The complete implementation, advanced multi-agent training pipelines, and empirical benchmark results for this next stage are hosted in the active [**Phase 2 Development Repository**](https://github.com/mehrsamiz/Multi-Agent-boardgame-RL).

While Phase 1 establishes a rigorous deterministic baseline using classical adversarial search, **Phase 2** expands the system's horizon by transitioning from hand-tuned heuristic trees toward autonomous learning and global optimization frameworks. To mitigate the severe state-space explosion ($>36!$ combinations) and handle complex multi-phase mechanics, the architecture is upgraded with the following paradigms:

### 1. Tabular & Feature-Engineered Reinforcement Learning
* **State Space Abstraction & Aggregation:** Transitioning away from exact grid tracking toward permutation-invariant macro-structural forms (`q_learning_exact`) and high-velocity 3D sparse vector compressions (`q_learning_compact`) to guarantee rapid policy convergence.
* **Topographic Feature Approximation:** Mapping environment dynamics into dense 6-dimensional topographic spaces (`q_learning_hybrid`) backed by shaped multi-tiered reward functions ($R = 15 \cdot \Delta \mathcal{B} + \dots$) and forward simulation engines.
* **Optimistic Initial Value Exploration:** Driving exploration via inherent, variance-free curiosity mechanisms ($Q_0 \in [20.0, 30.0]$) to eliminate rigid $\epsilon$-greedy decay constraints during training.

### 2. Global Evolutionary Parameter Optimization
* **Real-Valued Genetic Algorithms:** Modeling high-level strategic dimensions (flexibility, blocking, asset velocity) as a 7-gene dictionary of real-valued chromosomes, optimized via uniform stochastic crossover and generational mutation matrices (`genetic_heuristic`).
* **Deterministic Combinatorial Action Trees:** Integrating exact, exhaustive look-ahead trees within the evolutionary offline loop (`generic_offline_training`) to completely eliminate stochastic fallbacks during non-linear, multi-phase companion choice environments (e.g., Ramsay, Jon Snow, Jaqen Hghar).

### 3. Asynchronous Persistence Engine
* Implementing high-velocity binary state serialization (`pickle`) integrated directly into native runtime interpreter `atexit` registries, ensuring seamless training continuity and policy backups upon execution termination.
