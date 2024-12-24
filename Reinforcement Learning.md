Reinforcement Learning is another type of Machine learning Paradigm with few key differences from other Machine Learning Paradigms like Supervised or Unsupervised Learning.

- Unlike the Supervised and Unsupervised Paradigms where we try to optimize the model to make predictions based on the optimal pattern it learned using a given dataset, clustering or dimensionality reduction, RL main goal is maximize the rewards our agent, policy produces while interacting with a given environment.
- Another key difference is in Sup/UnSup the observations are typically independent, and in RL consecutive observations are generally correlated. In some types of RL algorithms like DQN for example we sometimes add a bit of randomness in a way of Replay buffers.
- One big difference between Supervised and RL is, when training supervised models we have a clear way to tell the model what is right and what is wrong with the help of datasets for example. Unlike this in RL the model explores on its on and corrects itself while trying to maximize the rewards.
- Unlike Unsupervised Learning where the model does not have a given dataset so it learns patterns on its on with the help of clustering and dimensionality reduction, RL does have some kind of a supervision with the help of rewards, +rewards means good -rewards means bad.

In general the main goal of RL is optimize our model to maximize the rewards.

There are Two main types of Reinforcement Learning Algorithms: [[RL On-Policy]] and [[RL Off-Policy]] ,
The main difference between them is the way of training the target network,
and the relation between the behavior policy and target policy.

The most fundamental RL Algorithm is Q-Learning(off-policy) using q-table.
Q-Table is a lookup table in which the rows represent the states, the columns represent the possible actions and each cell represents the Q-Value.
The Q-Value represents the **expected future cumulative reward** by taking the specific action,
In simple words it takes the immediate reward and iteratively adds future rewards by discounting them with discount factor.
The discount factor is responsible for the importance of future rewards.

|             | **Action** 1 | **Action** 2 |
| ----------- | ------------ | ------------ |
| **State 0** | Q-Value      | Q-Value      |
| **State 1** | Q-Value      | Q-Value      |



Each Q-Value is updated based on the following algorithm:

> [!Q-Value]
> Q(state) += lr * [reward + (discount_rate * max(Q(next_state))) - Q(state)]
or simply
Q(state) = Q(state) + lr * TD_Error

Q-Learning uses the TD Error to improve the q-values iteratively,
TD Error calculated by subtracting the current state Q-value from next_states max Q-value
and measures the mistake made in its current estimate.

The main problem of Q-Learning is scaling to environments with large number of states and actions.

To deal with large environment scaling **Deep Q-Network** was introduced.
Instead of using a table for q-values we use a neural network to calculate the q-values.

Example of DDQN(Off-Policy) on CartPoleV2 environment:
[Double DQN](https://github.com/NickSlm/ML/blob/main/CartPoleV2.ipynb)

Example of Policy Gradient(On-Policy) on LunarLanderV3 environment:
[Policy Gradient](https://github.com/NickSlm/ML/blob/main/Lunar%20LanderV3.ipynb)