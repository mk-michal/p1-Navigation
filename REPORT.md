#Procedure
As the main algorithm the deep q-network was used for an agent.
Neural network acts as a function approximator of our problem, receives state space values and outputs action values with max value being our desired action.

More information about deep-q reinforcement learning could be in 
```
Mnih, V., Kavukcuoglu, K., Silver, D. et al. 
Human-level control through deep reinforcement learning. 
Nature 518, 529–533 (2015). 
https://doi.org/10.1038/nature14236
```

Also `ExperienceReplay` was used in order to avoid correlation between consecutive observation.
We are storing tuples in `Replay buffe` and taking observation from there by random.

We also apply calculate Q-target neural network using so-called soft update. 
This simply means that the Target neural network stays fixed for a couple of iteration and is updated afterwords.

We used Two linear layers in our neural network with hidden layers of 64 units. 
This networks gives us great combination of speed and accuracy of the network so we can easilly train on CPU.


#Experiments
Final results of the training can be seen in `model/results.txt`.
Desired result was to get score more than `13` over 100 consecutive iterations.
This goal was achieved after 500th iteration and with highest score after iteration 1700 -> `16.81`.


Oscilation of the results could be seen on `model/results_plot.png`. 
We could see, that agent stopped learning (or remained more or less the same) around epoch 1000.


We tried to tune various hyperparameters like Epsilon decay, learning rate or Tau. 
Parameters values for the final model were:  
```
class AgentHyperparams:
    BUFFER_SIZE = int(1e5)  # replay buffer size
    BATCH_SIZE = 64  # minibatch size
    GAMMA = 0.99  # discount factor
    TAU = 1e-3  # for soft update of target parameters
    LR = 5e-4  # learning rate
    UPDATE_EVERY = 4  # how often to update the network
    
class ModelHyperparams:
    EPSILON = 0.8
    N_EPISODES = 2000
    MAX_T = 1000
    EPS_START = 1.0
    EPS_END = 0.01
    EPS_DECAY = 0.995

```
#Possible Enhancements
1. deeper network:
    Our neural network contains only 3 layers, therefore could be described as shallow
   Adding couple of layers  could increase accuracy of our model, but could lead to slower training 
   and we could no longer train on cpu only.
2. hyperparameter tuning:
    We believe that we could achieve the goal (score over 13 in 100 consecutive episodes) in much 
   lower number of iterations. Epsilon could be decreasing faster or learning rate could be higher 
   to achieve faster convergence. This could lead however to divergence as well or exploading gradient.
