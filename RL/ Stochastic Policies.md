#! https://zhuanlan.zhihu.com/p/267273306
# Stochastic Policies

## 1. Categorical Policies

sampling:
>Given the probabilities for each action, frameworks like PyTorch and Tensorflow have built-in tools for sampling. 

Log-Likelihood
>$$log\pi _{\theta}(a|s) =  log[P_{\theta}(s)] _{a}$$

## 2. Diagonal Gaussian Policies
sampling:
> Given the mean action $\mu_{\theta}(s)$ and standard deviation $\sigma_{\theta}(s)$, and a vector $z$ of noise from a spherical Gaussian ($z \sim \mathcal{N}(0, I)$), an action sample can be computed with
> 
>$$ a = \mu_{\theta}(s) + \sigma_{\theta}(s)\odot z$$
>
>where $\odot$ denotes the elementwise product of two vectors. 

Log-Likelihood. 
>The log-likelihood of a k -dimensional action a, for a diagonal Gaussian with mean 
$\mu = \mu_{\theta}(s)$ 
and standard deviation 
$\sigma = \sigma_{\theta}(s)$, 
is given by
>
>$$\log \pi_{\theta}(a|s) = -\frac{1}{2}\left(\sum_{i=1}^k \left(\frac{(a_i - \mu_i)^2}{\sigma_i^2} + 2 \log \sigma_i \right) + k \log 2\pi \right)$$



