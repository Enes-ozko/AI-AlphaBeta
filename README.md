# 🔴🟡 Connect 4 AI (Alpha-Beta Pruning)

> **Context:** Artificial Intelligence Project (ENSISA).
> **Goal:** Develop a competitive AI for Connect 4 using game theory algorithms "from scratch".
> **Tech Stack:** Python, NumPy, Tkinter.

## 📌 Project Overview
This project implements a **Minimax algorithm** optimized with **Alpha-Beta pruning** to play Connect 4 against a human or another AI.
The AI anticipates moves up to a variable depth (default 4-6) and evaluates the board using a custom heuristic function.

## 🧠 Algorithmic Core
The AI decision-making process relies on three pillars:

### 1. Minimax & Alpha-Beta
* **Minimax:** Simulates the game tree. The AI (Max) tries to maximize its score, assuming the opponent (Min) plays perfectly to minimize it.
* **Pruning:** We drastically reduced computation time by implementing **Alpha-Beta pruning**, which cuts off branches that cannot possibly influence the final decision.
* **Optimization:** Search order is optimized by prioritizing the **center column**, allowing the pruning to happen much earlier in the tree traversal.

### 2. Heuristic Evaluation (The "Brain")
Since solving the full game tree ($4.5 \times 10^{13}$ positions) is impossible in real-time, we use a **Sliding Window** approach (4 cells) to score the board.

**Scoring Strategy (Defensive):**
We prioritized blocking the opponent over attacking.
* **Victory:** +100,000 points.
* **Critical Danger (Opponent has 3+1):** **-120 points**.
* **Opportunity (AI has 3+1):** +100 points.
* *Logic:* Since $|-120| > 100$, the AI will always choose to block a loss rather than attempting a risky win.

### 3. Architecture (MVC)
The code follows a clean Object-Oriented structure:
* **`Board` (Model):** Handles grid logic using **NumPy** for memory efficiency. Contains the heuristic engine.
* **`Connect4` (Controller/View):** Manages the game loop and **Tkinter** GUI rendering.

## 👥 Authors
* **Enes Ozkosar**
* Omar Lidalt

---
*Note: The full project report (Architecture, Heuristics, Complexity Analysis) is available in French in the `docs/` folder.*