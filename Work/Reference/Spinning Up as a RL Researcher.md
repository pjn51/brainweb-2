---
author:
genre: STEM
---
# OpenAI: Spinning Up as a RL Researcher
`LINKS:` [[OpenAI]] | [Source](https://spinningup.openai.com/en/latest/spinningup/spinningup.html)
 #wip 

---
This is an article provided by OpenAI about how to get into [[reinforcement learning]].

## Part 1: Key Concepts in RL
In an nutshell, RL models learn by trial and error. They've been used to teach computers to control robots, both in simulation and in real life. They've also been used to create AIs for strategy games such as Go and Dota. 

The main characters of RL are the *agent* and the *environment.* At every stage of interaction, the agent percieves a sometimes limited view of the environment, and acts. The environment changes when the agent acts on it, and can also change independently of the agent's action. 

After acting, the agent percieves a *reward* signal from the environment. This number tells the agent how good or bad the environment's state is, and the agent attempts to maximize its cumulative reward, called the *return.* 

A *state* is a complete description of the environment. An *observation* is a partial description of the environment, which may omit information. In deep RL, states and observations are represented by *a real-valued vector, matrix, or higher-order tensor.* We represent state with $s$ and observation with $o$.

When the agent is able to observe the complete environment, we say that the environment is *fully observed* and when the agent only has partial observation, we say the environment is *partially observed.* 

The set of all valid actions in a given environment is called the *action space.* These spaces can be discrete, if there is a finite set of actions possible, or they can be continuous if an infinite amount of actions are possible. Whether an action space is discrete or continuous ha profoind effects on which algorithms we can use in that situation.

### Policies
A *policy* is a rule used by the agent to decide which action to take. It can be either deterministic...

$$a_t = \mu(s_t)$$

...or stochastic (meaning that it's determined probabilistically).

$$a_t ~ \pi(\cdot|s_t)$$

The above equations are describing how an action *a* at time *t* is determined.

In deep RL, we deal with *parameterized policies*. These policies are determined by a set of paramaters such as the weights and biases of a [[neural network]]. We can adjust these parameters via an optimization algorithm. We use the subscript $\theta$ to represent the parameters.

$$a_t = \mu_\theta(s_t)$$
$$a_t ~ \pi_\theta(\cdot|s_t)$$

### Deterministic Policies
For example, here's the code one would need to build a simple deterministic policy using PyTorch:

```python
pi_net = nn.Sequential(
					nn.Linear(obs_dim, 64),
					nn.Tanh(),
					nn.Linear(64,64),
					nn.Tanh(),
					nn.Linear(64,act_dim)
)
```

This creates a multi-layer perception network with two hidden layers of size 64 and [[tanh]] activation functions. If `obs` is a [[NumPy]] array with a batch of observations, `pi_net` can be used to obtain a batch of actions as follows:

```python
obs_tensor = torch.as_tensor(obs, dtype=torch.float32)
actions = pi_net(obs_tensor)
```

### Stochastic Policies
If you want to use a stochastic policy, we need to discuss *categorical* and *diagonal Gaussian* policies. Categorical policies are used in discrete action spaces, and diagonal Gaussian policies can be used when the action space is continuous. 

There are two computations that are important for using and training these sorts of policies:
1. Sampling actions from a policy
2. Computing log likelihood of particular actions, $log \ \pi_\theta(a|s)$

A categorical policy is like a classifier over discrete actions. We build the NN for a categorical policy just like we did earlier. At the end of the network, we use a [[softmax]] to convert the logits into probabilities. Frameworks like PyTorch and Tensorflow have built-in tools for sampling. 

A multivariate Gaussian distribution is described by a mean vector and a covariance matrix. A diagonal gaussian policy relies on the *diagonal* Gaussian distribution, where the covariance matrix only has entries on the diagonal.

