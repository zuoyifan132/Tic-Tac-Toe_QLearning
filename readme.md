#<center>Tic-Tac-Toe with Q Learning<center/>

## Usage

To run the game with a random agent, which chooses a random available position, and put mark there. run

```shell
python main.py
```

for a terminal interface. or run

```shell
python main_gui.py
```

for a graphic interface. You will need the PyQt5 library to support it. To install it, run

```shell
pip install PyQt5
```



**After you have finished your agent**, you can run

```shell
python main.py -a MLPlayer
```

or

```shell
python main_gui.py -a MLPlayer
```

to test your agent manually.

##Files included:

- `main.py`: This is the main script to run the game in the terminal interface, where you can play against the agent.
- `main_gui.py`: This is the main script to run the game in the graphic interface, where you can play against the agent.
- `player.py`: This file contains the implementation of the `MLPlayer` class, which is the Q-learning based agent.
- `qtable.pickle`: This file is the saved Q-table, which is used to load the saved Q-table for training the agent.

1. Requirements:
   - Python 3.6 or higher.
   - PyQt5 library (only required for running the game in the graphic interface).

2. Running the game:
   - To play against the Q-learning based agent, run `python main.py -a MLPlayer` in the terminal or `python main_gui.py -a MLPlayer` in the graphic interface.
   - To train the Q-learning based agent, run `python train.py`.

3. Q-learning algorithm:
   - The Q-learning algorithm is used to train the agent to play Tic-Tac-Toe. The agent maintains a Q-table, which stores the Q-values for each state-action pair.
   - During each game, the agent chooses an action based on the current state and the Q-table. It updates the Q-value of the previous state-action pair based on the reward received and the maximum Q-value of the next state.
   - The agent uses an epsilon-greedy strategy to balance exploration and exploitation. It selects a random action with probability epsilon, and selects the action with the maximum Q-value with probability 1-epsilon.

4. MLPlayer class implementation:
   - The `MLPlayer` class implements the Q-learning based agent. It has the following methods:
     - `__init__(self, mark, epsilon=0.1, alpha=0.5, gamma=0.9)`: Initializes the Q-table and sets the values of epsilon, alpha, and gamma.
     - `get_action(self, state, available_actions)`: Chooses an action based on the current state and the Q-table.
     - `update_table(self, state, action, next_state, reward)`: Updates the Q-value of the previous state-action pair based on the reward received and the maximum Q-value of the next state.
     - `save_table(self, filename)`: Saves the Q-table to a file.
     - `load_table(self, filename)`: Loads the Q-table from a file.

   - The `get_action` method chooses an action based on the current state and the Q-table. It uses the epsilon-greedy strategy to balance exploration and exploitation. If the agent is exploring, it chooses a random action from the available actions. If the agent is exploiting, it selects the action with the maximum Q-value from the Q-table.

   - The `update_table` method updates the Q-value of the previous state-action pair based on the reward received and the maximum Q-value of the next state. It uses the Q-learning update rule:

     ```
     Q(s, a) = Q(s, a) + alpha * (reward + gamma * max(Q(s', a')) - Q(s, a))
     ```
     
     where `s` is the current state, `a` is the current action, `s'` is the next state, `a'` is the action taken in the next state, `alpha` is the learning rate, and `gamma` is the discount factor.
     
   - The `save_table` and `load_table` methods are used to save and load the Q-table to and from a file, respectively. This is useful for persisting the learned Q-values between runs of the program.