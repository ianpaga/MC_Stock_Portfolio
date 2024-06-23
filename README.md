Monte Carlo Simulation of Stock Portfolio
====================

## Description: 

Monte Carlo (MC) is a computational simulation that relies on a *repeated random sampling* to estimate numerical results.

More often than not, solutions to a system in physics (or finance) are not deterministic. If we place the same input in more complex models with different underlying 
distributions (non-normal multi-variate distributions), one gets different results. Thus, there are no exact mathematical solutions for problems of this complexity.
Therefore, we rely on MC simulations by repeatedly drawing random samples from a normal distribution.

## Figures:
![stocks_gif](https://github.com/ianpaga/MC_Stock_Portfolio/assets/57350668/b198c95f-80d0-4a0f-b959-965e913b6a2e)

# Methods & Assuptions:

We will be assuming daily returns are distributed by a **Multivariate Normal Distribution** $R_t \sim \mathrm{MND}(\mu,\Sigma)$, 
where $\mu$ is the mean and $\Sigma$ is the covariance matrix (the covariance matrix generalizes the notion of variance to multiple dimensions).
**Cholesky Decomposition** is used to determine **Lower Triangular Matrix** (this is our covariance matrix):

$$
L \in LL^T = \Sigma
$$

$$
R_t = \mu + L \cdot Z_t
$$

$$
Z_t \sim N(0,I)
$$

where $Z_t$ are the samples from a normal distribution, and $I$ is the Identify Matrix.

Notes: simple for MC for stocks when we have a MND. We use Cholesky to represent the daily returns by that formula,
we take a bunch of uncorrelated sampled data that we sampled from a ND and we are correlating them through the use
of this Lower Triangle Matrix $L$. The Cholesky decomposition introduces a correlation between the assets.

## Requirements: 
1. Pandas
2. NumPy
3. datetime
4. pandas_datareader (pip install --upgrade pandas_datareader)
5. scipy.stats
6. matplotlib
7. yfinance (pip install --upgrade yfinance)
