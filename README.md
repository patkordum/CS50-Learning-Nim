# CS50-Learning-Nim

# Nim Game with Q-Learning AI

This project implements the classic game of Nim, where players take turns removing objects from piles, with the goal of avoiding being the player who takes the last object. The game is extended with an AI agent that learns to play using Q-learning.

## Table of Contents

- [Installation](#installation)
- [How to Play](#how-to-play)
- [AI Training](#ai-training)
- [Game Rules](#game-rules)
- [Code Overview](#code-overview)
- [License](#license)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/nim-qlearning.git
   cd nim-qlearning
   ```

2. Ensure you have Python installed (version 3.x recommended).

3. No additional dependencies are required for running the code.

## How to Play

You can play the Nim game against the AI by running the following command:

```bash
python play.py
```

The game will prompt you to choose a pile and the number of objects to remove. The AI will then make its move, and this continues until there is a winner.

## AI Training

Before playing against the AI, you can train it by running:

```python
from play import train

ai = train(10000)  # Train the AI with 10,000 games
```

This will allow the AI to learn the optimal strategy over time. You can adjust the number of training games as desired.

## Game Rules

- The game starts with a set of piles, each containing a certain number of objects.
- Two players take turns removing any number of objects from a single pile.
- The player forced to take the last object loses the game.

## Code Overview

### `Nim` Class

- **Initialization**: 
  - Initializes the game board with a default set of piles `[1, 3, 5, 7]`.
  - Manages the current player and determines the winner.

- **Methods**:
  - `available_actions(piles)`: Returns all valid actions from the current state.
  - `other_player(player)`: Switches between player 0 and player 1.
  - `move(action)`: Executes the given action and updates the game state.

### `NimAI` Class

- **Initialization**: 
  - Initializes the AI with Q-learning parameters (`alpha` and `epsilon`).
  - Stores the Q-values for state-action pairs.

- **Methods**:
  - `update(old_state, action, new_state, reward)`: Updates the Q-values based on the outcome of an action.
  - `get_q_value(state, action)`: Retrieves the Q-value for a given state-action pair.
  - `update_q_value(state, action, old_q, reward, future_rewards)`: Applies the Q-learning update rule.
  - `best_future_reward(state)`: Determines the best possible future reward from a given state.
  - `choose_action(state, epsilon)`: Chooses an action based on the epsilon-greedy strategy.

### `train(n)` Function

- Trains the AI by playing `n` games against itself and updating the Q-values.

### `play(ai, human_player=None)` Function

- Allows a human player to play against the trained AI, with the option to choose which player moves first.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
