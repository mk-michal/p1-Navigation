# Navigation project
This project is written as a part of Udacity's Deep Reinforcement Learning Nanodegree program.

In this project, I will train an agent that will navigate in a large squered world.
Example:

[image1]: https://user-images.githubusercontent.com/10624937/42135619-d90f2f28-7d12-11e8-8823-82b970a54d7e.gif "Trained Agent"

A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana.  Thus, the goal of the agent is to collect as many yellow bananas as possible while avoiding blue bananas.  

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around agent's forward direction.  Given this information, the agent has to learn how to best select actions.  Four discrete actions are available, corresponding to:
- **`0`** - move forward.
- **`1`** - move backward.
- **`2`** - turn left.
- **`3`** - turn right.


In order to run the training process, run 
``` 
python run_agent_navigation.py
```

Final weights for the trained neural network are saved as `model/weights.pth`

To run trained model and see the results of training script, run 
```
python eval_agent.py --n-runs 4
```

Banana_Linux environment was provided by Udacity Deep Learning nanodegree course.

## Approach
In order to solve this problem, deep-q learning using neural network was used.


Results are saved as `model/results.txt` and chosem hyperparameters as `model/hyperparameters.json`.

More detailes about the procedure and algorithms used are given in REPORT.md

## Setup
Banana environment requires python 3.6

To run the training or evaluation part install requirements in `requirements.txt` using pip as

```
pip install -r requirements.txt
```
