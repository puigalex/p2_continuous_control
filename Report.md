[//]: # (Image References)

[actor_critic]: ./resources/Actor-Critic.png "Actor Critic"
[Scores]: ./resources/score_graph.png 
[Scores2]: ./resources/score_graph2.png 
[Scores3]: ./resources/score_graph.png


# Report for p2_continuous_control from Deep Reinforcement Learning Nano Degree

## Learning Algorithm

Deep Deterministic Policy Gradient is an algorithm in reinforcement learning that combines two approaches for deep reinforcement learning, Q-Learning and Policy based methods. As we learned from the previous lessons, Q-Learning is a good method to use in specific cases to teach agents, however if we have a continuous actions/state space this can become very complicated, of course we can try to discretise the problem, other solution is to use Policy based methods, in which we are able to estimate the optimal policy without the need to estimate the optimal value function. But in this case with DDPG we'll use an actor-critic agent in which we merge this two concepts in order to have a better balnce between our variance and bias.

This architecture consists of two main parts, the actor and the critic.

The critic is a NN that is in charge of evaluating the value function with the best action identified by the actor, then we calculate the advantage funcion to train the other NN that is the actor.

![][actor_critic]


The neural network I stablished at the end for this model are both a 4 layer network for the actor and the critic with ReLu as the activation function.

In DDPG we keep using a buffer os state action rewards tuples, but a new mechanism is added called soft update in which we start merging our regular and target, so we start slowly matching the weights we have on the regular network to the target one.



## Findings (Human Learning)

At the beggining even though I used the bipedal ddpg example as a template I had to do a lot of tweaking since I was not getting the results I wanted. 

First my agents were learning very slow completing 1 episode in a long time after some troubleshooting, mostly trimming the NN, I realized that my agents were learning after every timestep which made it incredibly slow, so I adapted the code for wait for every 16 time steps. After that learning was faster but increasing in score incredibly slow so in that part of the code I also added to train the agents (update_learn) 20 times every  16 time steps.

After this solution my agents learned better and faster, reaching the 30+ average score in episode 90. This issues I had took me about a week to solve but I think I ended up with a decent model. 

Modifying the neural network (in a conservative way due to GPU constraints on my local machine) resulted in minor variances, maybe reaching the 30+ in a couple of episodes before or increase the score by 0.5, this modifications were later scaled down again, in order to have what I considered a good tradeoff of performance and compute power consumption.

The architecture I had best results was with 400 & 300 hidden neurons in the actor and critic, with 512 & 256 I got the process acheived but at episode 263 vs the (400,300) where I got it done at step 172

![][Scores] 
</br>Scores with the best architecture

![][Scores2]
</br>Scores decreasing the number of time I train agenst after 20 timesteps (trained 10 times instead of 20)

![][Scores3]
</br>Scores with 512 & 256 neurons on the hidden layers.

## Ideas for future work

I'd like to give a try to the Crwaler environment mentioned on the project. Also keep changing the NNs architecture to see if there is some sort of relation between the complexity of the actos vs the critic, like "having a more complex critic proves better" or something along that line.

