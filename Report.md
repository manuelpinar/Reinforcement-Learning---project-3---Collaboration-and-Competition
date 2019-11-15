# Report
---
I used an reinforcement learning method called Multi-Agent Deep Deterministic Policy Gradient (MADDPG). This algorithm is a new population DRL algorithm. MADDPG is a kind of "Actor-Critic" method. Unlike DDPG algorithm which trains each agent independantly, MADDPG trains actors and critics using all agents information (actions and states). However, the trained agent model (actor) can make an inference independentaly using its own state.
The environment is episodic, and in order to solve the environment, your agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents).

## Environment
In this environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.

The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation. Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.

## Learning Algorithm
 I used the maddpg algorithm taking the agent from 'ddpg_agent.py' 
 
 We must take in account that when I call the function maddpg in the notebook 'Tennis.ipynb' the enter parameters of this function was modified in order to adapt the requirements of this project. 
 
### Using

- num_agents = 2
- n_episodes (int): maximum number of training episodes
- max_t (int): maximum number of timesteps per episode

Where

`n_episodes=3000`, `max_t=1000`


###Hyperparameters
```
BUFFER_SIZE = int(1e6)  # replay buffer size
BATCH_SIZE = 512        # minibatch size
GAMMA = 0.99            # discount factor
TAU = 4e-2              # for soft update of target parameters
LR_ACTOR = 5e-4         # learning rate of the actor
LR_CRITIC = 4e-4        # learning rate of the critic
WEIGHT_DECAY = 0.0      # L2 weight decay

EPSILON = 1.0           # initial noise
EPSILON_DECAY = 5e-3    # noise decay
```

The main modification in this 'ddpg_agent.py' is in OUNoise parameters:

I used 'theta=0.15' and 'sigma=0.2' in front of the parameters used in the last project.

After some modifications I observed I hadn't significative improvements when I tried to modify other parameters like bacth_size or lr_actor and lr_critic also I hadn't significative improvements.
Neither when I tried modify the number of the layers of my 'model.py'

When I found a great improvement was movind the random_seed, setting finally in 0.5.


### Model

The model was extracted of the example provided in ddpg-pendulum of the DRLND repository and modified the number of units of the actor and the critic:

Actor ----  fc1_units=200, fc2_units=100
Critic ---- fc1_units=200, fc2_units=100

Being  ----> fc1_units (int): Number of nodes in first hidden layer
             fc2_units (int): Number of nodes in second hidden layer

## RESULTS
```
Episode 1	Average Score: 0.100
Episode 2	Average Score: 0.100
Episode 3	Average Score: 0.100
Episode 4	Average Score: 0.100
Episode 5	Average Score: 0.080
Episode 6	Average Score: 0.083
Episode 7	Average Score: 0.071
Episode 8	Average Score: 0.063
Episode 9	Average Score: 0.056
Episode 10	Average Score: 0.059
Episode 11	Average Score: 0.063
Episode 12	Average Score: 0.058
Episode 13	Average Score: 0.061
Episode 14	Average Score: 0.064
Episode 15	Average Score: 0.065
Episode 16	Average Score: 0.061
Episode 17	Average Score: 0.063
Episode 18	Average Score: 0.064
Episode 19	Average Score: 0.061
Episode 20	Average Score: 0.058
Episode 21	Average Score: 0.055
Episode 22	Average Score: 0.057
Episode 23	Average Score: 0.063
Episode 24	Average Score: 0.064
Episode 25	Average Score: 0.066
Episode 26	Average Score: 0.067
Episode 27	Average Score: 0.064
Episode 28	Average Score: 0.066
Episode 29	Average Score: 0.067
Episode 30	Average Score: 0.068
Episode 31	Average Score: 0.066
Episode 32	Average Score: 0.064
Episode 33	Average Score: 0.062
Episode 34	Average Score: 0.063
Episode 35	Average Score: 0.061
Episode 36	Average Score: 0.059
Episode 37	Average Score: 0.058
Episode 38	Average Score: 0.059
Episode 39	Average Score: 0.060
Episode 40	Average Score: 0.061
Episode 41	Average Score: 0.062
Episode 42	Average Score: 0.063
Episode 43	Average Score: 0.064
Episode 44	Average Score: 0.065
Episode 45	Average Score: 0.068
Episode 46	Average Score: 0.068
Episode 47	Average Score: 0.073
Episode 48	Average Score: 0.076
Episode 49	Average Score: 0.076
Episode 50	Average Score: 0.077
Episode 51	Average Score: 0.077
Episode 52	Average Score: 0.078
Episode 53	Average Score: 0.078
Episode 54	Average Score: 0.080
Episode 55	Average Score: 0.082
Episode 56	Average Score: 0.084
Episode 57	Average Score: 0.085
Episode 58	Average Score: 0.085
Episode 59	Average Score: 0.088
Episode 60	Average Score: 0.089
Episode 61	Average Score: 0.094
Episode 62	Average Score: 0.094
Episode 63	Average Score: 0.094
Episode 64	Average Score: 0.096
Episode 65	Average Score: 0.097
Episode 66	Average Score: 0.100
Episode 67	Average Score: 0.099
Episode 68	Average Score: 0.099
Episode 69	Average Score: 0.099
Episode 70	Average Score: 0.099
Episode 71	Average Score: 0.097
Episode 72	Average Score: 0.097
Episode 73	Average Score: 0.100
Episode 74	Average Score: 0.100
Episode 75	Average Score: 0.099
Episode 76	Average Score: 0.104
Episode 77	Average Score: 0.105
Episode 78	Average Score: 0.120
Episode 79	Average Score: 0.120
Episode 80	Average Score: 0.121
Episode 81	Average Score: 0.120
Episode 82	Average Score: 0.125
Episode 83	Average Score: 0.132
Episode 84	Average Score: 0.139
Episode 85	Average Score: 0.153
Episode 86	Average Score: 0.156
Episode 87	Average Score: 0.164
Episode 88	Average Score: 0.163
Episode 89	Average Score: 0.171
Episode 90	Average Score: 0.173
Episode 91	Average Score: 0.176
Episode 92	Average Score: 0.187
Episode 93	Average Score: 0.200
Episode 94	Average Score: 0.199
Episode 95	Average Score: 0.198
Episode 96	Average Score: 0.203
Episode 97	Average Score: 0.228
Episode 98	Average Score: 0.230
Episode 99	Average Score: 0.232
Episode 100	Average Score: 0.235
Episode 100	Average Score: 0.235
Episode 101	Average Score: 0.235
Episode 102	Average Score: 0.236
Episode 103	Average Score: 0.237
Episode 104	Average Score: 0.237
Episode 105	Average Score: 0.238
Episode 106	Average Score: 0.244
Episode 107	Average Score: 0.245
Episode 108	Average Score: 0.256
Episode 109	Average Score: 0.261
Episode 110	Average Score: 0.277
Episode 111	Average Score: 0.278
Episode 112	Average Score: 0.298
Episode 113	Average Score: 0.298
Episode 114	Average Score: 0.314
Episode 115	Average Score: 0.339
Episode 116	Average Score: 0.340
Episode 117	Average Score: 0.346
Episode 118	Average Score: 0.358
Episode 119	Average Score: 0.371
Episode 120	Average Score: 0.397
Episode 121	Average Score: 0.398
Episode 122	Average Score: 0.417
Episode 123	Average Score: 0.421
Episode 124	Average Score: 0.426
Episode 125	Average Score: 0.426
Episode 126	Average Score: 0.427
Episode 127	Average Score: 0.445
Episode 128	Average Score: 0.452
Episode 129	Average Score: 0.452
Episode 130	Average Score: 0.452
Episode 131	Average Score: 0.453
Episode 132	Average Score: 0.459
Episode 133	Average Score: 0.479
Episode 134	Average Score: 0.483
Episode 135	Average Score: 0.509

Environment solved in 35 episodes!	Average Score: 0.51
```

![](https://github.com/manuelpinar/Reinforcement-Learning---project-3---Collaboration-and-Competition/blob/master/maddpg.png?raw=true)

### Future improvements

We could use another algorithms like PPO this algorithm was proposed in the project tips on slack. 
Also, we could consider use other type of model, using more layers and preprocessing the data in order to improve the results.
