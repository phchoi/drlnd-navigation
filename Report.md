# Banana Navigation Project Report

This project is one of the assignment of Udacity Deep Reinforcement Learning Nanodegree. Student will need to make use of an agent to pick up yellow banana from a Unity game environment. When the agent successfully picked up one yellow banana it will be given reward score of +1. But on the contrary, if the agent picked up a blue banana then it will be given a reward of -1. Our goal is to achieve score of 13 in less than 2000 episodes.

# Environment

The environment is based on a Unity game environment with 4 actions and 37 states. The agent will need to learn from the combinations of action, states and rewards.

```
Unity Academy name: Academy
        Number of Brains: 1
        Number of External Brains : 1
        Lesson number : 0
        Reset Parameters :
		
Unity brain name: BananaBrain
        Number of Visual Observations (per agent): 0
        Vector Observation space type: continuous
        Vector Observation space size (per agent): 37
        Number of stacked Vector Observation: 1
        Vector Action space type: discrete
        Vector Action space size (per agent): 4
        Vector Action descriptions: 
```

# Learning Algorithm
To attain the goal, we will need to train the agent. Considering the game environment is a relatively big continuous space so it is kinda hard to use traditional Reinforcement Learning technique like Monte-Carlo Method or Sarsa to train the agent. End up DQN, Deep Q-Network is choosen with below neural network layers.

```
    Fully connected layer - input: 37 (state size = 37) output: 128
    Fully connected layer - input: 128 output 128
    Fully connected layer - input: 127 output: (action size=4)
```

Parameters of DQN:

```
    Maximum steps per episode  : 1000
    Starting epsilion          : 1.0
    Ending epsilion            : 0.01
    Epsilion decay rate        : 0.995
    Buffer Size                : 100000
    Batch Size                 : 64
    Gamma (Discount factor)    : 0.99
    TAU (Soft Update) rate     : 0.001
    Learning Rate              : 0.0005
    How often to update network: 4
```

Apart from using the above DQN, we also implement a memory replay mechanism such that the agent will be able to randomly pick previous states to re-learn when certain numbers of steps had been accumulated.

# Results

Here is the number of episode rans and its corresponding scores level. From the test runs, it can usually achieves score of 13 within range 450 episodes to 550 episodes.

Episode 100	Average Score: 1.03
Episode 200	Average Score: 3.88
Episode 300	Average Score: 6.83
Episode 400	Average Score: 9.66
Episode 500	Average Score: 12.40
Episode 516	Average Score: 13.06
Environment solved in 515 episodes!	Average Score: 13.06

I also tried training the agent with more number of episodes like 2000, but the number of scores reached maximum at around 14 to 15 and no longer to get any higher even i raised the number of episodes to 4000. 

# Idea of future works
The DQN itself is very effective in solving problem like this. However, to improve the results further (i.e. achieve score of 13 with smaller numbers of episodes or even aim for higher scores), we will need to elaborate other techniques like Dueling DQN, Double DQN and Prioritized Experience Replay.

Also, right now the states is obtained through the games (with 37 states returned for each action), may be making a transition to train the agent with visual states can be also very interesting and challenging.