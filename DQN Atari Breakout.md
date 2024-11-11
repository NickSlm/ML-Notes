
In Atari Breakout Environment each Frame is represented as an rgb_array image.
Because 1 Frame does not tell us about velocity of the environment, we stack multiple Frames to represent 1 Step.
In this Example 1 step = 4 Frames.

Run the main loop for N number of iterations for example n_iterations = 50,000
Each **Iteration** we run for a **total** of **27,000 steps** - ( 27,000 is the env max steps )
Each run of the environment is called an episode, the episode ends when the state of the environment either reaches the max steps or is done (truncated/terminated).
When an episode is done but iteration did not reach the total N steps, new episode will be started.
Each step we will be collecting the experience which is a tuple of **(state, action, reward, next_state, done)** and adding it to the experience memory to later sample it for training.
We will be using a "Epsilon Greedy Policy" to get the action for each step.


There are **two types** of **experience memory**: **random replay buffer** and **prioritized replay buffer**.
In random replay buffer we randomly sample N experiences and in prioritized we have weights in each experience and based on the highest weights we sample the experiences.
The weights typically used are the absolute TD (Temporal Difference) error.

Every **4 steps** we will be **training** our **Q_Value Model**, and every **N iterations** we will be **updating** our **Target Model**.

The Q_Value Model Is built the following way:

	    keras.layers.Input(shape=env.observation_space.shape)
	    keras.layers.Lambda(lambda obs: tf.cast(obs, np.float32) / 255.)
	    keras.layers.Conv2D(32, (8,8), strides=4, activation="relu", data_format="channels_first")
	    keras.layers.Conv2D(64, (4,4), strides=2, activation="relu", data_format="channels_first")
	    keras.layers.Conv2D(64, (3,3), strides=1, activation="relu", data_format="channels_first")
	    keras.layers.Flatten()
	    keras.layers.Dense(512, activation="relu")
	    keras.layers.Dense(4) # N actions

