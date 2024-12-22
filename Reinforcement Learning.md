Reinforcement Learning is another type of Machine learning Paradigm with few key differences from other Machine Learning Paradigms like Supervised or Unsupervised Learning.

- Unlike the Supervised and Unsupervised Paradigms where we try to optimize the model to make predictions based on the optimal pattern it learned using a given dataset, clustering or dimensionality reduction, RL main goal is maximize the rewards our agent, policy produces while interacting with a given environment.
- Another key difference is in Sup/Unsup the observations are typically independent, and in RL consecutive observations are generally correlated. In some types of RL algorithms like DQN for example we sometimes add a bit of randomness in a way of Replay buffers.
- One big difference between Supervised and RL is, when training supervised models we have a clear way to tell the model what is right and what is wrong with the help of datasets for example. Unlike this in RL the model explores on its on and corrects itself while trying to maximize the rewards.
- Unlike Unsupervised Learning where the model does not have a given dataset so it learns patterns on its on with the help of clustering and dimensionality reduction, RL does have some kind of a supervision with the help of rewards, +rewards means good -rewards means bad.

In general the main goal of RL is optimize our model to maximize the rewards.

#### Reinforcement Learning Terms ####
**Step:** 
A single interaction between an agent and the environment.
The following happens with each step.
The agent observes the current env state
and takes an action based on our policy.
The agent outputs will typically be next_state, reward, done.
For example in LunarLander the state will be the position of the Lander,
and the actions will be:
no fire, fire left, fire right, fire down.

**Episode:**
A single Episode is made of a sequence of steps and it end when the environment reaches a terminal state (terminated and or truncated).
For example a single Episode of the LunarLander environment will be full game from start to finish.

**Iteration:**
An iteration is a single cycle of learning process.
Each iteration we train the model on the collected data we got from each step taken.
typically each iteration runs N number of episodes before we train the models.

