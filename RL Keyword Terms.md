#### Reinforcement Learning Terms ####

**Behavior Policy:**
A policy that decides on which action to take on a given state,
it can do that randomly, deterministically, stochastically or a combination of both.
Example:
```
def greedy_epsilon_policy(state, epsilon):
	if np.random.rand() < epsilon:
		return env.action_space.sample()
	q_values = model.predict(state[np.newaxis])
	return np.argmax(q_values[0])
```

**Target Policy:**
A policy, typically it will be a neural network (In q-learning it will be a table) which calculates the q-value for each state, action and it is the policy that is being trained.
Example:
```
model = keras.models.Sequential([
	keras.layers.Dense(32,activation="relu", input_shape=[n_inputs]),
	keras.layers.Dense(32,activation="relu),
	keras.layers.Dense(n_ouputs)
])
```

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

