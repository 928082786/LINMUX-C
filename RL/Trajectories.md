#! https://zhuanlan.zhihu.com/p/267411301
# Trajectories

$\tau = (s_0, a_0, s_1, a_1, ...).$

$s_0 \sim \rho_0(\cdot)$

$s_{t+1} = f(s_t, a_t)$

$s_{t+1} \sim P(\cdot|s_t, a_t)$

> Trajectories are also frequently called **episodes** or **rollouts**.

---
# Reward and Return

$r_t = R(s_t, a_t, s_{t+1})$

The goal of the agent is to maximize some notion of cumulative reward over a trajectory, but this actually can mean a few things. We'll notate all of these cases with $R(\tau)$, and it will either be clear from context which case we mean, or it won't matter (because the same equations will apply to all cases).

$$R(\tau) = \sum_{t=0}^{\infty} \gamma^t r_t$$

# RL Problem
>  Whatever the choice of return measure (whether infinite-horizon discounted, or finite-horizon undiscounted), and whatever the choice of policy, the goal in RL is to select a policy which maximizes expected return when the agent acts according to it.

## Policy Function 

 $$P(\tau|\pi) = \rho_0 (s_0) \prod_{t=0}^{T-1} P(s_{t+1} | s_t, a_t) \pi(a_t | s_t)$$

## Expect Function

$$J(\pi) = \int_{\tau} P(\tau|\pi) R(\tau)
=E_{\tau \sim \pi}{R(\tau)}$$

## optimal policy

$$\pi^* = \arg \max_{\pi} J(\pi)$$

# Value Function

1. The On-Policy Value Function


    $$V^{\pi}(s) =  E_{\tau \sim \pi}[{R(\tau)\left| s_0 = s\right.}]$$



2. The On-Policy Action-Value Function

    $$ Q^{\pi}(s,a) = E_{\tau \sim \pi}[{R(\tau)\left| s_0 = s, a_0 = a\right.}]$$

3. The Optimal Value Function

    $$V^*(s) = \max_{\pi} E_{\tau \sim \pi}[{R(\tau)\left| s_0 = s\right.} ]$$

4. The Optimal Action-Value Function

    $$Q^*(s,a) = \max_{\pi} E_{\tau \sim \pi}[{R(\tau)\left| s_0 = s, a_0 = a\right.}]$$

>  There are two key connections between the value function and the action-value function that come up pretty often:
>  $$V^{\pi}(s) = E_{a\sim \pi}[{Q^{\pi}(s,a)}$$
> $$V^*(s) = \max_a Q^* (s,a).$$
---
$$a^*(s) = \arg \max_a Q^* (s,a).$$

# Bellman Equations
The basic idea behind the Bellman equations is this:

    The value of your starting point is the reward you expect to get from being there, plus the value of wherever you land next.

The Bellman equations for the on-policy value functions are

$$V^{\pi}(s)  = E_{a \sim \pi \  \ s'\sim P}[{r(s,a) + \gamma V^{\pi}(s')}]$$
$$Q^{\pi}(s,a) 
= E_{s'\sim P}[{r(s,a) + \gamma}  E_{a'\sim \pi}{Q^{\pi}(s',a')}]$$

The Bellman equations for the optimal value functions are

$$ V^*(s) = \max_{a} E_{s'\sim P}[{r(s,a) + \gamma V^*(s')}]$$
$$ Q^*(s,a) = E_{s'\sim P}[{r(s,a) + \gamma \max_{a'} Q^*(s',a')}]$$

## Advantage Functions

    The advantage function corresponding to a policy  describes how much better it is to take a specific action  in state s

$$ A^{\pi}(s,a) = Q^{\pi}(s,a) - V^{\pi}(s)$$

>The advantage function is crucially important to policy gradient methods.


