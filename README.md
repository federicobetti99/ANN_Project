# CS-456 Artificial Neural Networks, Mini-project 1
This repository contains the implementation of Q-Learning and Deep Q-Learning (DQN) algorithms for training an agent to play Tic-Tac-Toe.

## Requirements
Requirements for the needed packages are available in requirements.txt. To install the needed packages, please run:
```
pip install -r requirements.txt
```

## Repository Description
* `code` - Folder containing code and auxiliary files
  * `figures` - Contains the plots presented in the report
  * `results` - Contains the Python dictionaries with the results for each question
  *  `Reproduce.ipynb` - Notebook for reproducibility of the results
  *  `deep_q_learning.py` - Implementations for the Deep Q-Learning Algorithm
  *  `q_learning.py` - Implementations for the Q-Learning Algorithm
  *  `utils.py` - Utilities and support functions
  *  `tic_env.py` - Implementation of the environment
  *  `visualization.py` - Plot functions
  *  `train_multiple_runs.py` - Functions to perform multiple training runs and compute average statistics
* `report` - Folder containing the report
* `requirements.txt` - Requirements text file 

## Usage and reproducibility
### Reproducing the results in the report
We provide a unique notebook containing the answers to all the questions of the project (except for Question 6, the theoretical one). The notebook should be used as follows.

To obtain the plots presented in the report, please set in the very first cells
```python
train = False
load = not train
```
This loads our results from the Python dictionaries provided in the folder `results` and, for each question, shows firstly the plot presented in the report, and in the following cell a plot of all the experimented values. 

To perform training without loading from the provided dictionaries, please set
```python
train = True
load = not train
```
We remark that, since several values of the parameters have been experimented and since we averaged the performance over multiple runs, this might take a very long time (more than 1 day).

For the questions concerning the optimal values of the performance measures, our results are obtained from averaging over 10 training runs for Q-Learning and 4 runs for Deep Q-Learning. Thus, for these questions:
  - we show a sample run for the optimal values of the parameters, to show the correct training of the agent;
  - we load the averaged results from the dictionaries (for the same parameters configuration as above). These are the values presented in the report.

### Example of usage
- Q-Learning training
```python
env = TictactoeEnv()  # set the environment
alpha = 0.05  # learning rate
gamma = 0.99  # discount factor
epsilon_exploration = 0.1  # exploration rate
test_freq = 250  # testing frequency during training
against_opt = True  # or self_practice = True, depending on the desired training method
Q, stats = q_learning(env, alpha=alpha, gamma=gamma, epsilon_exploration=epsilon_exploration, test_freq=test_freq, against_opt=against_opt)  # return Q-values and training stats
```

- Deep Q-Learning training
```python
env = TictactoeEnv()  # set the environment
lr = 1e-4  # learning rate
gamma = 0.99  # discount factor
epsilon_exploration = 0.1  # exploration rate
test_freq = 250  # testing frequency during training
against_opt = True  # or self_practice = True, depending on the desired training method
model, stats = deep_q_learning(env, lr=lr, gamma=gamma, epsilon_exploration=epsilon_exploration, test_freq=test_freq, against_opt=against_opt)  # return model network and training stats
```

## Report
The report can be found in pdf format in the folder `report`.

## Authors
- Federico Betti
- Ivan Bioli
