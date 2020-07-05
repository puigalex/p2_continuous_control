[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/43851024-320ba930-9aff-11e8-8493-ee547c6af349.gif "Trained Agent"


# Project 2: Continuous Control

### Introduction

This is my submission for the 2nd project for the Udacity deep reinforcement learning nano degree, in this project I did the code to solve the [Reacher](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) environment with 20 agents with DDPG (Deep Deterministic Policy Gradients)

![Trained Agent][image1]

### Environment spec

The reacher environment contains 20 agents that consist of an arm with two joints, each agent receives a reward a 0.1 every time step the end of the arm is in the target location. 

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

### Success Criteria

In order to consider that the agents have learned through DDPG they must obtain an average score (average between the 20 agents) of 30+ through at least 100 episodes.

It is important to have this score for at least 100 episodes since in some cases we can obtain the 30+ score for several episodes but if some parameter of the algorithm is implemented inneficiently then out of nowhere the agents can drop their scores well bellow the 30 mark.


### Requirements

In order to run this project the following packages and environments should be installed in the machine. To do so, the following steps should be followed

1. Download the environment from one of the links below.  You need only select the environment that matches your operating system:

    - **_Version 2: Twenty (20) Agents_**
        - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
        - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
        - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
        - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)
    

2. Place the file in the DRLND GitHub repository, in the `p2_continuous-control/` folder, and unzip (or decompress) the file. 

3. Install the requirements in the requirements.txt file 

### Files

There are 3 main files in this project, each one is needed in order to train, evaluate and save the agent.

* **model.py**  This file contains the neural net used to train the agent, hyperparameters can be changed to experiment the solutions, with the restriction of respecting the input of 33 (state size) and the output of 4 (action space)
* **agent.py** File containing the actor/critic class, this class is the one in charge of creating the agent, selecting the actions to take given a specific state, buffering actions and learning (teaching the agent)
* **train.ipynb** This notebook takes you cell by cell in which we start the Unity environment, instantiate the agent and manage the interactions between the Agent class and the environment.




