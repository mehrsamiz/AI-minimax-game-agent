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

## 🛠️ Installation & Requirements

### Prerequisites
* Python 3.8 or higher
* Pygame

### Setup
1. Clone this repository:
   ```bash
   git clone [https://github.com/mehrsamiz/AI-project-phase1.git](https://github.com/mehrsamiz/AI-project-phase1.git)
   cd AI-project-phase1


# Running the Game

To evaluate the performance of the Minimax agent against the stochastic baseline framework, execute main.py from the root directory using the following command:

```Bash
python main.py --player1 "my_agent" --player2 "random_agent"
```

# Evaluation Framework

The agent's performance was evaluated against a stochastic baseline engine (random_agent.py) to quantify decision-making capability under varying initialization constraints. The custom Minimax agent consistently achieves an optimal win-rate convergence, demonstrating high tactical stability across a diverse spectrum of randomized initial board configurations.

# ⏭ Pipeline Horizon: Phase 2
