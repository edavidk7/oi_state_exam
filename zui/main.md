# ZUI

Status: Done

## Requirements

Metody prohledávání stavového prostoru, algoritmy. Reprezentace znalostí a rozhodování s nepřesnou znalostí. Dvouhráčové hry. 

• Známé systémy umělé inteligence: DeepBlue, Watson, AlphaGo, Eliza, Shakey, DQN.

• Formální reprezentace problému AI: problém mnohorukého banditu, MDP, POMDP, hra v
rozšířené formě.

• Metody prohledávání stavového prostoru: DFS, BFS, ID-DFS, Dijkstra, A*.

• Algoritmy posilovaného učení: policy evaluation, policy improvement, policy iteration, value
iteration, Q-learning.

• Algoritmy pro řešení her dvou hráčů: minimax, alpha-beta prořezávání, negamax, negascout,
MCTS.

• Strukturovaná reprezentace znalostí: CSP, Scheduling, Situation calculus, STRIPS.

• Neurčitost v AI: maximalizace očekávané utility, Bayesovo pravidlo, Bayesovské sítě.

• Řešení POMDP: PBVI, HSVI.

## Known Successful AI Algorithms and Systems

### DeepBlue

The first computer system (Hardware + Infrastructure + Algorithms) to beat a chess grandmaster. Based on search, no ML involved yet. Beat Kasparov in 1997. 

- Main Algorithm was NegaScout (fast, heuristic-driven search)
- Additional state space reduction techniques/optimizations (transposition tables, iterative deepening)
- Heavily parallelized over specific hardware (custom chips for chess play)
- Opening and Endgame databases tuned by chess grandmasters
- Overall a brute-force based approach allowed the standard, relatively simple textbook algorithms to scale (200 million positions per second)

### Watson

One of the first successful/complete-package NLP systems, developed by IBM. It could extract semantic information from even unstructured documents, operated chatbots. Beat humans in the quiz “jeopardy!” in 2011. 

- Ensemble of expert algorithms
- Logistic regression as posterior model for question answering
- Decision trees
- Bayesian modeling

### AlphaGo

First successful attempt to beat a human champion at Go, a combinatorially much more complex game than chess. In 2016, AlphaGo defeated a human professional player 4-1. Considered much more important than chess, because Go requires explicit reasoning/intuition as “searching” over all potential moves is not tractable (for people or computers). Core idea was the use of deep learning (reinforcement learning) to learn a prior knowledge-guided search.

- Deep CNNs that process the board as an image (policy and value function).
- First, networks were pretrained in a supervised manner from human-annotated data (expert moves)
- Next, they were finetuned using reinforcement learning from self-play
- During self-play, multiple instances of the networks play against each other and the gradient updates try to reinforce the best strategy and suppress the losing ones
- The learned policies guided an MCTS-based search algorithm to allow for some online exploration/planning
- The xxZero variants learned purely with RL, without supervised pretraining

### Eliza

An early natural-language chatbot, designed to mimic a psychologist. Published in 1966.

- Pattern Matching
- Transformation rules: identify keyword → relate to context → transform the keywords + context

### Shakey

A “complete” multi-purpose autonomous robot, developed by Stanford Research Institute 1966-1972. Automatic control, vision, perception, planning, NLP. Name because the movements were shaky. Introduced numerous new technologies. 

- Fully integrated perception, reasoning, planning, navigation, control
- Camera, rangefinders, collision sensors, electric motors
- System programmed in Lisp
- Very high-level planning and reasoning: STRIPS
- Environment navigation: $A^*$ algorithm (new development)
- NLP command processing
- Hough transform for perception: geometrical primitives in polar parameter space

### DQN

A critical success in combining reinforcement learning (Q-learning) and Deep Learning. The objective was to learn an RL policy for playing Atari Games, whose state space is mainly represented by RGB images, making it intractable to use standard tabular Q-learning. Instead, the   action-value function is approximated with neural network with multi-class outputs representing the buttons on the Atari controller. Published in 2015, it achieved human or even superhuman levels of performance on many Atari games.

- Q-Learning is the main learning algorithm
- The Q-function is approximated by a CNN
- $\epsilon$-greedy exploration policy
- DQN tricks: frozen target parameters to stabilize gradients and experience replay to reuse old experiences and improve sample complexity

## Search

![image.png](assets/image.png)

Okay, but what do the formal representation?

![image.png](assets/image%201.png)

There are some fundamental models to which we apply search:

![image.png](assets/image%202.png)

### Markov Decision Process (MDP)

![image.png](assets/image%203.png)

### Partially-Observable MDP (POMDP)

![image.png](assets/image%204.png)

### Extensive Form Games (EFG)

![image.png](assets/image%205.png)

### Solving a Deterministic MDP

Say that we have a deterministic MDP without stochastic effects. 

![image.png](assets/image%206.png)

![image.png](assets/image%207.png)

Some problems there: we want to find the best sequences, choosing any state to expand does not guarantee that we find the best action. We also need to be able to detect returning to a previously visited state (otherwise we would end up in an infinite loop).

![image.png](assets/image%208.png)

![image.png](assets/image%209.png)

BFS/DFS can be intractable for realistic problems. Uniform-cost search is Dijkstra’s algorithm. 

![image.png](assets/image%2010.png)

![image.png](assets/image%2011.png)

In practice, use a hash set for fast lookup of already evaluated states. 

![image.png](assets/image%2012.png)

The iterative deepening procedure always searches a whole level in either the edge count space or the cost space. By moving this upper bound, we are guaranteed to find the goal state with the minimum number of actions. Be careful! If we come back to a state we previously found with some cost, we might have a lower cost and could have to re-expand it.

Uniform-cost search has a caveat!

![image.png](assets/image%2013.png)

What is a heuristic?

![image.png](assets/image%2014.png)

There is a catch! If the heuristic underestimates the cost of a state, and we expand it sooner (instead of a state whose apparent cost is higher, but true cost might be lower), we could arrive in the goal state through a sub-optimal solution.

An admissible heuristic guarantees this won’t happen: 

![image.png](assets/image%2015.png)

We can now define the whole $A^*$ procedure:

![image.png](assets/image%2016.png)

Note we have to add the accumulated cost to guarantee optimality (goal state is popped from the PQ iff it is the one with lowest accumulated cost). 

![image.png](assets/image%2017.png)

![image.png](assets/image%2018.png)

In other words, with an admissible heuristic, we’re guaranteed to always expand the state with the  lowest apparent cost, which however isn’t lower than the real cost. At worst, we can expand a seemingly good node, but then in reality it’s bad, we accumulate a lot of incurred costs and then then stop expanding this path. Note that the goal state is always expanded with apparent cost being the sum of incurred costs along the way and nothing else.

![image.png](assets/image%2019.png)

Or in other words, the decrease in heuristic estimates between neighboring nodes is always less than the actual cost incurred for that transition.

![image.png](assets/image%2020.png)

The consistent heuristic ensures that we don’t open a state more than once (which would happen if we later find a cheaper path to a previously explored state). 

Some extra modifications:

![image.png](assets/image%2021.png)

![image.png](assets/image%2022.png)

![image.png](assets/image%2023.png)

## Reinforcement learning

![image.png](assets/image%2024.png)

Standard model for the world in RL is a Markov Decision Process. The simplest instance used to study RL algorithms are Multi-armed bandits.

### Multi-Armed Bandits

![image.png](assets/image%2025.png)

We would like to learn how to maximize the expected return from the bandit environment. This means we have to learn which levers to pull to obtain the highest reward.

![image.png](assets/image%2026.png)

How to gain and learn at the same time?

![image.png](assets/image%2027.png)

![image.png](assets/image%2028.png)

This is the basis of Q-learning methods. In this case, we form the estimate as a simple sample mean. However, we still need to learn how to explore the environment

![image.png](assets/image%2029.png)

Okay, but we still need a way to learn the estimate. We will do this with a running mean.

![image.png](assets/image%2030.png)

Alternatively, it can also be good to use EWA, because it will track even non-stationary distributions.

![image.png](assets/image%2031.png)

UCB ~ Consider the “standard deviation” of the samples and add it to the current estimate for a more optimistic value. As an action is explored more and more, its empirical sttdev goes down and it makes way for an another, less explored action.

Conclusion for bandits:

![image.png](assets/image%2032.png)

### General MDPs

The behavior learned by the agent is encapsulated into a policy, a function or probability distribution mapping a state in the MDP to a single action or some distribution over actions. 

![image.png](assets/image%2033.png)

Our goal is to maximize the expected **return** in every state. The return can be defined in various ways.

![image.png](assets/image%2034.png)

We split this based on the underlying task we’re trying to solve:

![image.png](assets/image%2035.png)

![image.png](assets/image%2036.png)

To model the expected return for each state of the MDP, we use a value function.

![image.png](assets/image%2037.png)

Note that the value function is parameterized by the policy (the expectation depends on the probability of taking an action in the next state, which in turn depends on the policy again.

We also define an optimal policy/optimal value function:

![image.png](assets/image%2038.png)

![image.png](assets/image%2039.png)

Bellman Equation for the Value Function:

![image.png](assets/image%2040.png)

Recall the greediness of the optimal policy wrt. the optimal value function. We can derive a closed-form of the optimal value and action-value functions through bellman equations.

![image.png](assets/image%2041.png)

![image.png](assets/image%2042.png)

If we want to solve these equations exactly, we need to know the exact model of the environment. If we do, we can define some basic methods for finding the value function (solving the equations) iteratively.

### Policy Evaluation:

Given a fixed policy, find the value function.

![image.png](assets/image%2043.png)

Why does it work? Because the mapping is contractive and converges to a unique fixed point for any initialization

![image.png](assets/image%2044.png)

### Policy Iteration

An iterative process where we interleave improvement and evaluation steps in order to find the optimal policy/value function. If we know that some action has the highest action-value function in a given state, by setting the policy to be deterministic in this action we monotonously improve the policy’s value function.

![image.png](assets/image%2045.png)

### Value Iteration

We can merge the 2 steps of Policy Iteration into one. In every state, set the value function to the highest action-value function in that state (greedy, deterministic). This effectively merges the two steps, skipping the policy improvement step (it is equivalent).

![image.png](assets/image%2046.png)

### Q-learning

Off-policy temporal difference learning. We don’t know the underlying dynamics, we only try to learn from collected samples. 

TD Method:

![image.png](assets/image%2047.png)

One-step Q-learning

![image.png](assets/image%2048.png)

There are some potential problems: maximization bias (keeps selecting the currently best action, which may not be the best globally, especially with noise), keeps propagating downstream to other states. Solution is Double Q-Learning.

### RL Summary

![image.png](assets/image%2049.png)

## Games

Games differ from search in a key aspect - there are more agents affecting the environment (state of the game).

![image.png](assets/image%2050.png)

Good to know

![image.png](assets/image%2051.png)

We will focus only on games with the following properties:

- two players
- zero-sum (strictly competitive) - one’s win is the second one’s loss
- perfect information, fully observable (chess, go, tic-tac-toe)

How to represent an **Extensive Form Game**?

![image.png](assets/image%2052.png)

A history of the game can be understood as an action sequence executed up to a state of the game. The per-player indexing simply says the history (from the set $H_1 \subset H)$ ends at a point where player 1 should make a move.

![image.png](assets/image%2053.png)

### Minimax algorithm

![image.png](assets/image%2054.png)

The minimax algorithm simply swaps between 2 operations depending whose move it is currently. The utility values are defined for MAX (the player who started evaluating the search tree at the root).

This algorithm can be cumbersome, we can “prune” subtrees if we e.g. know that the MAX player got something (say 3 from the example above), while MIN finds a minimum lower than this value (say 2 in the middle node). Regardless of what lower value MIN finds (lower than 2), MAX will never choose this as it can get 3 elsewhere, therefore it does not make any sense to expand this branch further. We can formalize this

### Alpha-Beta Pruning

![image.png](assets/image%2055.png)

We keep track of both the upper and lower bound on the value of the game. In every turn of the MAX player, we keep the maximum value found from the nodes below. Whenever we cross the upper bound set by the MIN player, we prune and end the search. If our chosen value would be discarded by MIN, the whole subtree can be pruned and discarded too. The MIN player keeps a minimum, the situation is symmetrical. If our minimum is lower than the lower bound from MAX, we know MAX wouldn’t choose our node and we can again prune.

### Negamax

![image.png](assets/image%2056.png)

A variant of Alpha-Beta search, only difference is that instead of changing the operations, we take turns in flipping the signs and the bounds, which has the same effect mathematically.

### NegaScout

We can save even more time by setting the bounds to some narrower values, pruning earlier.

![image.png](assets/image%2057.png)

Example

![image.png](assets/image%2058.png)

![image.png](assets/image%2059.png)

Simply put, whenever we violate the interval set initially, we know that the true value is bounded by this new value, depending on the cross bound either higher (was pruned in MAX after crossing the upper bound) or lower (was pruned in MIN for crossing the lower bound)

Can we systemize this?

![image.png](assets/image%2060.png)

![image.png](assets/image%2061.png)

![image.png](assets/image%2062.png)

First give the best action a chance to find its true utility, then shortcut and see if re-searching is needed.

The overall algorithm is as follows:

MAX

![image.png](assets/image%2063.png)

It makes sense → first evaluate full, break or shrink window, evaluate with null window, perform a full window search if necessary. Note we don’t re-search if the value would be lower (we are maximizing).

MIN

![image.png](assets/image%2064.png)

The inverted behaviour for minimization

### Game Solving vs Game Playing

![image.png](assets/image%2065.png)

### Games with Chance

![image.png](assets/image%2066.png)

In unbounded case, we cannot do anything, negative values will skew the expected utility from chance nodes. With non-negative, we can do more, the expected value is indicative enough.

### Monte Carlo Tree Search

![image.png](assets/image%2067.png)

Only select-expand is performed in a guided way, the simulation is usually random (to not consume too many resources).

In the selection part, we need to select actions that are promising in that state. 

![image.png](assets/image%2068.png)

In the expansion part, we create new nodes of interest

![image.png](assets/image%2069.png)

We then simulate from the expanded node all the way until we find any leaf of the game tree. Then, take the utility in that leaf and propagate it back to the newly expanded and previously selected nodes (similar to bandits, simply update the estimates).

![image.png](assets/image%2070.png)

### AlphaGo

![image.png](assets/image%2071.png)

![image.png](assets/image%2072.png)

![image.png](assets/image%2073.png)

MCTS in AlphaGo works as follows:

![image.png](assets/image%2074.png)

## Constraint Satisfaction Programming, Scheduling

The previous approaches were not specifically tied to an exact problem, instead, they were general frameworks for solving different problems of the same high-level class (games, MDPs). We can look into approaches that are tailored to a very specific problem.

![image.png](assets/image%2075.png)

Example 

![image.png](assets/image%2076.png)

![image.png](assets/image%2077.png)

Variable = Queen, Domain = Allowed Values, Constraints = Relationships between feasible values

Constraint is defined in its most general form (set of tuples)

More examples:

![image.png](assets/image%2078.png)

Example CSP formulation of the N-Queens Problem:

![image.png](assets/image%2079.png)

The answer is not difficult - it simply becomes a large search tree

![image.png](assets/image%2080.png)

### CSP with binary constraints

We can reformulate any k-ary constraint into a binary constraint. 

![image.png](assets/image%2081.png)

Say we have $x_1 - x_2 + 3x_3 \leq 0$, the valid solutions (in reals) is a hyperplane.

Every point on the plane is a 3-tuple of variables. Define $x_{\text{plane}}$ with the domain of all points that lie on the original plane. 

Now create only binary constraints like $(x_\text{plane})_1 = x_1$. Whenever we assign $x_1$, we force quality to the first coordinate of $x_\text{plane}$, which in turn forces the other variables to have only feasible values.

![image.png](assets/image%2082.png)

![image.png](assets/image%2083.png)

![image.png](assets/image%2084.png)

![image.png](assets/image%2085.png)

MRV: assign something, alter variables domains for assignment. On next expansion, pick the variable with smallest current domain. But here is a problem. What if we locally violate some constraint, remove the values from domains, but there is one more constraint that we haven’t touched, but violated by our domain pruning? Big problem!

![image.png](assets/image%2086.png)

![image.png](assets/image%2087.png)

This is simply BFS over the constrains over the just-altered variable.

![image.png](assets/image%2088.png)

![image.png](assets/image%2089.png)

## Logical Agents and Planning

### Logical Agents

Logical Agents are a way to symbolically perform reasoning and plan steps that have to be taken to achieve a certain goal.

![image.png](assets/image%2090.png)

Example: Monkey & Banana

![image.png](assets/image%2091.png)

We will use First Order Logic to derive predicates that describe the world and actions.

![image.png](assets/image%2092.png)

The actions themselves (environment dynamics) are defined axiomatically.

![image.png](assets/image%2093.png)

Frame axioms ensure that the state of the world is unchanged, or that objects retain their properties:

![image.png](assets/image%2094.png)

Once we have all of these definitions, we can give a logical statement describing the goal state and perform logical inference using reasoning techniques:

![image.png](assets/image%2095.png)

### Domain-Independent Planning

![image.png](assets/image%2096.png)

First, we need to establish what can be generalized and shared:

![image.png](assets/image%2097.png)

![image.png](assets/image%2098.png)

Where is this useful?

![image.png](assets/image%2099.png)

We can see this as finding a path in some transition graph, solvable by e.g. uniform cost search (dijkstra).

Some spaces are too large for this, and there are many situations where would like to apply the planning.

![image.png](assets/image%20100.png)

![image.png](assets/image%20101.png)

![image.png](assets/image%20102.png)

Sokoban Example

![image.png](assets/image%20103.png)

![image.png](assets/image%20104.png)

![image.png](assets/image%20105.png)

Okay, we now have a problem definition, how to solve it? 

![image.png](assets/image%20106.png)

In particular, we can use relaxation heuristics:

![image.png](assets/image%20107.png)

![image.png](assets/image%20108.png)

So we removed all bad effects from the actions, making the problem simpler. Okay, now lets construct the solution and graph and solve the planning problem

![image.png](assets/image%20109.png)

What this means: In every step, check what preconditions hold (what atoms are true) and add the available actions (whose preconditions are met). Repeat this until all atoms for the goal state are true.

![image.png](assets/image%20110.png)

![image.png](assets/image%20111.png)

Okay, what is this simplified solution good for? Well, we now know how many steps we have to take to reach the goal in the simplest version of the problem. Or:

![image.png](assets/image%20112.png)

![image.png](assets/image%20113.png)

### Summary

![image.png](assets/image%20114.png)

## Rational decisionmaking under uncertainty

What does this mean? We want to make decisions that maximize the (expected) utility/reward under all possible outcomes. E.g. a lottery. For this, we need to measure and estimate the probability of events. Where do we need this?

![image.png](assets/image%20115.png)

![image.png](assets/image%20116.png)

It is important to know the Bayes’ theorem.

![image.png](assets/image%20117.png)

Okay, we can compute the probabilities of many events using the full joint distribution, but there is a big problem!

![image.png](assets/image%20118.png)

We can use a clever shortcut, leveraging the conditional independence of some terms. 

![image.png](assets/image%20119.png)

With this observation, lets formalize the concept with Bayesian Networks. 

![image.png](assets/image%20120.png)

How to perform inference?

![image.png](assets/image%20121.png)

![image.png](assets/image%20122.png)

What are some nice properties we can see and extract in BNs? 

![image.png](assets/image%20123.png)

Now the core task - computing the posterior given some evidence.

![image.png](assets/image%20124.png)

![image.png](assets/image%20125.png)

We need to marginalize over the internal parent variables.

![image.png](assets/image%20126.png)

Simplest instances of BNs: Spam filter (naive bayes), HMMs, Bayes Filter (HMM), KF

![image.png](assets/image%20127.png)

## Partially-Observable MDPs

![image.png](assets/image%20128.png)

The base definition is the same as vanilla MDP, however, we add the observation model (observation distribution), and we lose the perfect information about in which state the agent may be. We can only perform probabilistic inference.

![image.png](assets/image%20129.png)

This is just the classic bayes filtering scheme

### Example (to not go insane)

![image.png](assets/image%20130.png)

![image.png](assets/image%20131.png)

Okay, we now know how to extract the belief state. How should we act in an POMDP? Recall classic MDP:

![image.png](assets/image%20132.png)

![image.png](assets/image%20133.png)

We now compute the transition probability between beliefs, which is kinda hard to do (a belief is a probability distribution), so we are integrating over going from a probability distribution to some other probability distribution. But - this belief state can be easily represented by some continuous function, either a categorical distribution (n-dim vector on the standard simplex) or by parameters of a continuous distribution (e.g. normal - look at a bayes filter with normal distribution). The transition probability is then more or less given by the previous formula.

![image.png](assets/image%20134.png)

Alpha vectors simply put: a vector $\alpha =  (v_{s_1}, v_{s_2}, \dots, v_{s_n})$. The individual value functions are defined with respect **to the underlying MDP, and a fixed conditional action plan (conditioned on observations) which is stateless. Also can be imagined as a policy belief-tree.**

We then pick the highest alpha vector for the current belief over states, intuitively, we should follow the plan which maximizes the return based on the current expectation of states.

![image.png](assets/image%20135.png)

Lets decompose the sums one by one

1. Innermost sum: computes the *next* belief in $s^\prime$, and then computes the value of the t+1 step policy that takes action $a$ and receives observation $o$, this is the part of the conditional action-observation policy tree. We effectively prepend this action to the alpha vector $\alpha^\prime$ plan.
2. Outermost sum: over all possible observations, find the best alpha vector for this observation (in the *next* belief state induced by the observation)
3. The value of the belief is one for the action which maximizes the return over all possible belief states and all possible previous alpha vectors

To obtain the alpha vector corresponding to this value function, we need to remember the different observations and what actions would maximize the value in their respective belief states.

![image.png](assets/image%20136.png)

How to arrive at this number? For every available action we execute, we receive an observation, and for that observation, there exist exactly the number of strategies we had in the previous step. Because this selection is repeated for every observation, we exponent by the number of observations.

### Point-based Value Iteration

![image.png](assets/image%20137.png)

![image.png](assets/image%20138.png)

![image.png](assets/image%20139.png)

![image.png](assets/image%20140.png)

How it works:

We have some fixed belief points.

For each belief point, pick an action to find the value of. You do this by fixing the action, then for each alpha vector from the previous alpha vector enumerating over all possible observations and taking the expected value w.r.t. observation probability, you take the maximum over all alpha vectors.

This gives you a scalar value of each action. The new alpha vector is then defined as “take the best action found, and based on the received observation, follow the plan given by the best alpha vector for that situation from the previous step”.

### HSVI

![image.png](assets/image%20141.png)

![image.png](assets/image%20142.png)

![image.png](assets/image%20143.png)

![image.png](assets/image%20144.png)

![image.png](assets/image%20145.png)

Just read this retard: [https://arxiv.org/pdf/1207.4166](https://arxiv.org/pdf/1207.4166)