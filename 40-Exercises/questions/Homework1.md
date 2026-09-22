Here are the answers with brief justifications (in each case, identifiability means the map θ ↦ P_θ is injective — distinct parameter values must give distinct distributions of what you observe).

## Part (a)

**1. Poisson(λ), n iid observations — Identifiable**
Θ = (0,∞), P_λ = Poisson(λ)⊗n. The mean of the distribution is λ, so distinct λ's give distinct distributions.

**2. Exponential(λ), λ ≤ 10 — Identifiable**
Θ = (0,10]. Restricting the parameter space doesn't break injectivity: distinct λ, λ' ≤ 10 still give distinct exponential distributions. (Restricting Θ can never *destroy* identifiability, only preserve or create it.)

**3. Uniform[0,θ] — Identifiable**
Θ = (0,∞). The distribution has density 1/θ on [0,θ]; the support endpoint θ is recoverable (e.g., as the essential sup of X), so distinct θ give distinct distributions.

**4. Gaussian(μ,σ²), both unknown — Identifiable**
Θ = ℝ × (0,∞). The mean and variance of the observed Gaussian pin down (μ,σ²) exactly.

## Part (b)

**1. Sign of Gaussian(μ,σ²) — Not identifiable**
You only observe sgn(X) ∈ {−1,+1}, a Bernoulli variable with P(sgn(X)=1) = Φ(μ/σ). This probability depends only on the *ratio* μ/σ, not on (μ,σ²) separately. E.g., (μ,σ²) = (1,1) and (2,4) give the same value of μ/σ = 1, hence the exact same distribution of the observed data, but are different parameter values. So the parameter isn't recoverable.

**2. StatGen: Uniform[0,θ] output — Identifiable**
Same structure as (a).3: X_i ~ Uniform[0,θ] iid, and θ is recovered as the support endpoint. Distinct θ ⟹ distinct distributions.

**3. Census: indicator of commute ≥ 20 min, X ~ Exp(λ) — Identifiable**
You don't observe X directly, only Y = 1{X ≥ 20} ~ Bernoulli(p) with p = P(X≥20) = e^{−20λ}. The map λ ↦ e^{−20λ} is strictly decreasing (injective) on (0,∞), so different λ give different Bernoulli parameters p, hence different distributions of the observed data. λ is identifiable (even though you never see the exact commute times).

**4. Willy Wonka: 67 machines, Exp(λ), censored at T=500 — Identifiable**
The data consists of: which machines failed before T=500, and their exact lifetimes (machines still running at T are only known to have survived past T — right-censored). This is a truncated/censored exponential sample. The probability of failing before T is 1 − e^{−500λ}, and the density of an observed failure time x < 500 is proportional to λe^{−λx}. Both of these vary injectively with λ, so the joint law of the censored data determines λ uniquely — identifiable.

--- 

**Part (a): Var(X_i)**

$$\text{Var}(X_i) = p(1-p)$$

**Consistency of V̂:**

By the Law of Large Numbers, $\overline{X}_n \to p$ in probability. The function $g(x) = x(1-x)$ is continuous, so by the Continuous Mapping Theorem:
$$\hat V = g(\overline{X}_n) \to g(p) = p(1-p) = \text{Var}(X_i)$$

**Correct answer: V̂ is consistent because of the Law of Large Numbers and Continuous Mapping Theorem.**

---

**Part (b): Bias computation**

We need $\mathbb{E}[\hat V] = \mathbb{E}[\overline{X}_n] - \mathbb{E}[\overline{X}_n^2]$.

Since $\mathbb{E}[\overline{X}_n] = p$ and $\mathbb{E}[\overline{X}_n^2] = \text{Var}(\overline{X}_n) + p^2 = \dfrac{p(1-p)}{n} + p^2$:

$$\mathbb{E}[\hat V] = p - \frac{p(1-p)}{n} - p^2 = p(1-p)\left(1 - \frac{1}{n}\right) = p(1-p)\cdot\frac{n-1}{n}$$

So:
$$\mathbb{E}[\hat V] - \text{Var}(X_i) = p(1-p)\cdot\frac{n-1}{n} - p(1-p) = -\frac{p(1-p)}{n}$$

**Answer:**
$$\mathbb{E}[\hat V] - \text{Var}(X_i) = -\frac{\text{Var}(X_i)}{n}$$

---

**Unbiased estimator V′**

Since $\mathbb{E}[\hat V] = \dfrac{n-1}{n}\, p(1-p)$, multiply by $\dfrac{n}{n-1}$ to correct the bias (requires $n\ge 2$):

$$\boxed{V' = \frac{n}{n-1}\,\overline{X}_n\left(1-\overline{X}_n\right)}$$

Using the requested notation:

$$V' = \dfrac{n}{n-1}\,\text{barX\_n}\,(1-\text{barX\_n})$$

**Check:** $\mathbb{E}[V'] = \dfrac{n}{n-1}\cdot \dfrac{n-1}{n}p(1-p) = p(1-p)$ ✓, confirming $V'$ is unbiased for $p(1-p)$.

---


## Estimating the variance I

**Equivalent expression:** Expanding the square,
$$\frac{1}{n}\sum_{i=1}^n (X_i-\bar X_n)^2 = \frac{1}{n}\sum_{i=1}^n X_i^2 - \bar X_n^2$$

**Correct choice:** $\hat\sigma_n^2 = \dfrac{1}{n}\sum_{i=1}^n X_i^2 - (\bar X_n)^2$

**Is it unbiased?** **No.**
Indeed, $\mathbb{E}[\hat\sigma_n^2] = \dfrac{n-1}{n}\sigma^2 \neq \sigma^2$ (this is the classic bias of the MLE-type variance estimator — it under-estimates by a factor of $(n-1)/n$).

---

## Estimating the variance II

**Is $\hat\sigma_n^2$ consistent?** **Yes.**
By the LLN, $\frac1n\sum X_i^2 \to \mathbb{E}[X_i^2]$ and $\bar X_n \to \mu$ a.s./in probability; by the continuous mapping theorem, $\hat\sigma_n^2 \to \mathbb{E}[X_i^2]-\mu^2 = \sigma^2$. (Also, the bias $\to 0$ as $n\to\infty$.)

**Is $\hat\sigma_n^2$ asymptotically normal?** **Yes.**
*Why it suffices to assume $\mu=0$:* $\hat\sigma_n^2$ is invariant under a shift of the data, since $(X_i-\bar X_n) = (X_i-\mu) - (\bar X_n - \mu)$. So replacing $X_i$ by $X_i-\mu$ (which has mean 0) doesn't change $\hat\sigma_n^2$. This lets you write $\hat\sigma_n^2$ as a smooth function of $\frac1n\sum X_i^2$ and $\bar X_n$ applied to a mean-zero variable, and apply the CLT/delta method directly to get asymptotic normality of $\sqrt n(\hat\sigma_n^2-\sigma^2)$.

---

## Confidence interval for Gaussian mean: known variance

The standard level-95% CI centered at $\bar X_n$ is
$$I = \left[\bar X_n - q_{0.975}\frac{\sigma}{\sqrt n},\ \bar X_n + q_{0.975}\frac{\sigma}{\sqrt n}\right]$$
where $q_{0.975}$ is the $97.5\%$ quantile of $\mathcal N(0,1)$ (≈1.96).

**Length of $I$:**
$$|I| = 2\,q_{0.975}\,\frac{\sigma}{\sqrt n}$$

---

## Confidence interval for Gaussian mean: unknown variance

Replacing $\sigma$ by $\hat\sigma_n$ (which is only a *consistent*, not exact, estimator of $\sigma$) means the resulting interval $J$ no longer has exact (non-asymptotic) coverage $95\%$ — but by Slutsky's theorem combined with the CLT for $\bar X_n$, coverage still converges to $95\%$ as $n\to\infty$.

**Correct choice:** *Because $\hat\sigma_n^2$ is a consistent estimator, $J$ is a confidence interval of asymptotic level 95%.*

----

## (a) CLT normalization for Poisson

Since $\mathbb E[X_i]=\lambda$ and $\mathrm{Var}(X_i)=\lambda$, the classical CLT gives
$$\sqrt n\,\frac{\bar X_n-\lambda}{\sqrt\lambda}\ \xrightarrow{d}\ N(0,1).$$

So:
$$a_n=\sqrt{\dfrac{n}{\lambda}},\qquad b_n=\lambda$$

## (b) Expressing P(|Z|≤t)

$$\mathbf P(|Z|\le t)=\Phi(t)-\Phi(-t)=2\Phi(t)-1$$

i.e. **P(|Z| ≤ t) = 2·Phi(t) − 1**

## (c) Interval depending on λ

From (a), $a_n(\bar X_n-\lambda)\to Z$, so
$$\mathbf P\!\left(-1.96\le \sqrt{\tfrac n\lambda}(\bar X_n-\lambda)\le 1.96\right)\to .95.$$

Solving the inequality for the position of $\lambda$ relative to $\bar X_n$ (equivalently $|\bar X_n-\lambda|\le 1.96\sqrt{\lambda/n}$):

$$A = \bar X_n - 1.96\sqrt{\dfrac{\lambda}{n}}, \qquad B = \bar X_n + 1.96\sqrt{\dfrac{\lambda}{n}}$$

so $\mathcal I_\lambda=\left[\bar X_n-1.96\sqrt{\lambda/n},\ \bar X_n+1.96\sqrt{\lambda/n}\right]$.

## (d) Plug-in confidence interval

$\mathcal I_\lambda$ from part (c) isn't usable directly since it depends on the unknown $\lambda$. To get an actual (data-based) CI, we need a **consistent estimator of $\lambda$** plugged in for $\lambda$ (via Slutsky's theorem), so that the ratio of true to plugged-in value → 1.

Since $\bar X_n\xrightarrow{P}\lambda$ (LLN), $\bar X_n$ itself is a consistent estimator of $\lambda$, so it's legitimate to substitute $\lambda \to \bar X_n$ inside the square root.

Checking each option:
- $\mathcal J=[\bar X_n-1.96\sqrt{\lambda/n},\bar X_n+1.96\sqrt{\lambda/n}]$ — **Not valid**: still depends on the unknown $\lambda$, so it's not computable from data.
- $\mathcal J=[\bar X_n-1.96\sqrt{\bar X_n/n^2},\bar X_n+1.96\sqrt{\bar X_n/n^2}]$ — **Not valid**: wrong scaling ($n^2$ instead of $n$), doesn't match the CLT rate.
- $\mathcal J=[\bar X_n-1.96\sqrt{\bar X_n/n},\bar X_n+1.96\sqrt{\bar X_n/n}]$ — **Valid**: correct plug-in of the consistent estimator $\bar X_n$ for $\lambda$.
- $\mathcal J=[\bar X_n-1.96\sqrt{100/n},\bar X_n+1.96\sqrt{100/n}]$ — **Not valid**: uses the fixed constant 100 in place of $\lambda$, which only works if $\lambda=100$; it isn't a consistent estimator of a general unknown $\lambda$.

**Correct choice: only the third option**
$$\mathcal J=\left[\bar X_n-1.96\sqrt{\bar X_n/n},\ \ \bar X_n+1.96\sqrt{\bar X_n/n}\right]$$

----

## (a)

**P(M_n ≥ θ) = 0**
Since each $X_i \le \theta$ a.s., $M_n \le \theta$ always, and since the distribution is continuous, $P(M_n = \theta) = 0$.

**P(M_n ≤ θ − t) = ((θ−t)/θ)ⁿ**
$$P(M_n \le \theta-t) = P(X_1\le \theta-t,\dots,X_n\le\theta-t) = \left(\frac{\theta-t}{\theta}\right)^n$$

*Food for thought:* For any fixed $t>0$, this $\to 0$ as $n\to\infty$, so $M_n$ converges in probability to $\theta$ — i.e. $M_n$ is a consistent estimator of $\theta$.

## (b)

Using $s=\theta t/n$ in the formula above:
$$F_n(t) = P\big(n(1-M_n/\theta)\le t\big) = P\big(M_n \ge \theta(1-t/n)\big) = 1-\left(1-\frac{t}{n}\right)^n$$

$$\lim_{n\to\infty} F_n(t) = 1-e^{-t}$$

*Food for thought:* $n(1-M_n/\theta)$ converges in distribution to an **Exponential(1)** random variable.

## (c)

$$t = \ln(20)\approx 2.9957$$

**Reasoning:** From (b), $n(\theta-M_n)/\theta \xrightarrow{d} E \sim \text{Exp}(1)$. We want
$$P(\theta - M_n \le c) = P\left(\frac{n(\theta-M_n)}{\theta}\le \frac{nc}{\theta}\right)\to 1-e^{-nc/\theta} = .95$$
so $nc/\theta = -\ln(.05)=\ln(20)$, giving $c = \frac{\ln(20)}{n}\theta$, and plugging in $M_n$ for $\theta$: $c=\frac{t}{n}M_n$ with $t=\ln(20)$.

**Why plug-in works:** *By Slutsky's Theorem, we can combine convergence in distribution of $Y_n$ and in probability of $Z_n$ if $Z_n$ converges to a constant.* (Here $M_n/\theta \to 1$ in probability, a constant, so it can replace $\theta$ inside the asymptotically Exp(1) statistic.)

## (d)

The standard result for the max of $n$ iid Uniform$[0,\theta]$ is $\mathbb E[M_n] = \dfrac{n}{n+1}\theta$.

$$\mathbb E[M_n]-\theta = \frac{n}{n+1}\theta - \theta = -\frac{\theta}{n+1}$$
