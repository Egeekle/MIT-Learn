**1. Advantages of Modeling Assumptions**

Model 1 (Poisson) is determined by **one parameter** \(\lambda\).

Model 2 requires probabilities \(p_1,\dots,p_7\) (with one constraint that they sum to 1), so it effectively needs many more parameters.

✅ **Answer:** **It reduces the amount of unknowns needed for modeling.**

---

**2. Modelling a Binary Data Set**

Since \(Y\) can only be 0 or 1, its distribution is completely determined by

$$
p=P(Y=1).
$$

Then \(P(Y=0)=1-p\).

So only **one unknown parameter** is needed.

✅ **Answer:** **1**

---

**3. Approximating the unknown parameter**

By the **Law of Large Numbers**,

$$
\frac{1}{n}\sum_{i=1}^{n} Y_i \to E[Y]
$$

as \(n\to\infty\).

For binary data, the sample mean is also

$$
\frac{\text{total number of 1's}}{n}.
$$

The other options (\(Y_n\) and the median) do not generally converge to \(E[Y]\).

✅ **Select:**

* ☑ \(\dfrac{\text{total number of 1's}}{n}\)
* ☑ \(\dfrac{1}{n}\sum_{i=1}^{n} Y_i\)

❌ Do not select:

* \(Y_n\)
* \(\text{Median}(Y_1,\ldots,Y_n)\)

---

**Final Answers:**

1. **It reduces the amount of unknowns needed for modeling.**
2. **1**
3. **\(\dfrac{\text{total number of 1's}}{n}\)** and **\(\dfrac{1}{n}\sum_{i=1}^{n}Y_i\)**.

--- 


4.Cherry Blossom  Run

The average running time for the 2017 Cherry Blossom Run in Washington D.C was 98 minutes; the standard deviation was 17 minutes. Let X denote the running time, in minutes, of a random finisher. What is the best model for the distribution of X?

The best model is Normal Distribuiton:
$$X \sim \mathcal{N}(98, 17^2)$$
% or
$$X \sim \mathcal{N}(98, 289)$$


The Cherry Blosson dataset contains thousands of runners,and finishing time is treated as a continous quantitative variable.

The given information directly provides the parameters needed for a Normal model:the mean $\mu = 98$ and $\sigma = 17$


---

Here are the correct answers, in order:

### 5. Basic Statistical Model: Sample Space

The coin outcome is either heads \(=1\) or tails \(=0\).

✅ **Answer: \(\{0,1\}\)**

---

### 6. Smallest sample spaces

$X_1\sim\text{Poiss}(\lambda)$

A Poisson random variable can take values \(0,1,2,\ldots\).

✅ **Answer:**

$$
\boxed{\{x\in\mathbb Z:x\ge 0\}}
$$

$X_2\sim N(0,1)$

A Gaussian can take any real value.

✅ **Answer:**

$$
\boxed{(-\infty,\infty)=\mathbb R}
$$

$X_3\sim\exp(\lambda)$

An exponential random variable takes nonnegative real values.

✅ **Answer:**

$$
\boxed{[0,\infty)}
$$

$(X_4=\mathbb I(Y>0)$

An indicator function can only be \(0\) or \(1\).

✅ **Answer:**

$$
\boxed{\{0,1\}}
$$

---

### 7. Family of distributions and parameter set

The coin flips are Bernoulli distributed:

$$
X\sim\operatorname{Ber}(p).
$$

The unknown probability \(p\) can be **any value between 0 and 1**, inclusive.

✅ **Family:** **Bernoulli**

✅ **Parameter set:**

$$
\boxed{[0,1]}
$$

---

### 8. Statistical Model Definition Concept Check

Options:

1. $\left(\{1\},(\operatorname{Ber}(p))_{p\in(0,1)}\right)$
2. $\left(\{0,1\},(\operatorname{Ber}(p))_{p\in(0.2,0.4)}\right)$
3. Both
4. None

A Bernoulli distribution has possible outcomes \(0\) and \(1\). Therefore, the sample space \(\{1\}\) in option 1 does **not** contain all possible outcomes.

Option 2 has the correct sample space \(\{0,1\}\), and restricting \(p\) to \((0.2,0.4)\) is perfectly valid.

✅ **Answer: Option 2**

$$
\boxed{\left(\{0,1\},(\operatorname{Ber}(p))_{p\in(0.2,0.4)}\right)}
$$

---

### 9. Non-example of a Statistical Model

The important requirement is that the **sample space \(E\) must be fixed**, rather than changing with the parameter.

Option 1:

$$
\boxed{\left([0,a],(\mathcal U([0,a]))_{a>0}\right)}
$$

has a sample space \([0,a]\) that changes as \(a\) changes. Therefore, it is **not** a statistical model in the definition being used.

Option 2:

$$
\left(\mathbb R_+,(\mathcal U([0,a]))_{a>0}\right)
$$

has the fixed sample space \(\mathbb R_+\), so it is valid.

✅ **Answer:**

$$
\boxed{\left([0,a],(\mathcal U([0,a]))_{a>0}\right)}
$$


---

### 10. Parametric model for rock samples

You know:

* \(X_i\) are Gaussian.
* The mean satisfies \(\mu>0\).
* The variance is **known**: \(\sigma^2=0.23\).
* Each measurement can take any real value, so the sample space is \((-\infty,\infty)\).

Therefore, the model that incorporates **all** the information is

$$
\boxed{\left((-\infty,\infty),\{N(\mu,0.23)\}_{\mu>0}\right)}.
$$

For the question's distinction:

* A model with \(\mu\in\mathbb R\) and variance \(0.23\) is still a **formally valid larger model**, but it ignores the known fact \(\mu>0\).
* Models with unknown \(\sigma^2\) are also larger models that contain the true distribution, but they ignore the fact that the variance is known.

So, among the choices:

**(1) Formally valid:** all four *distinct* normal-family models shown are formally valid if “formally valid” means the true distribution is contained in the model.

**(2) Best incorporates all known information:**

$$
\boxed{\left((-\infty,\infty),\{N(\mu,0.23)\}_{\mu>0}\right)}
$$

If the duplicate-looking checkbox appears twice in your quiz, select the instances corresponding to that expression as required by the interface.

---

### 11. Censored exponential

For an exponential random variable with rate \(\lambda\),

$$
X\sim \operatorname{Exp}(\lambda),
$$

we have

$$
P(X>5)=e^{-5\lambda}.
$$

Since

$$
Y=\mathcal I(X>5),
$$

\(Y=1\) with probability \(e^{-5\lambda}\), and \(Y=0\) otherwise.

Thus

$$
Y\sim \operatorname{Bernoulli}(e^{-5\lambda}).
$$

So enter:

$$
\boxed{e^{-5\lambda}}
$$

**Answers:**

1. Best/full-information model: \(\boxed{((-\infty,\infty),\{N(\mu,0.23)\}_{\mu>0})}\)
2. \(\boxed{e^{-5\lambda}}\)



----


A continuación se detalla la resolución paso a paso para cada uno de los puntos solicitados:

---

### 1. Valor esperado de $X$ ($\mathbb{E}[X]$)

Dado que $X = Z X_1 + (1 - Z) X_2$, aplicamos linealidad de la esperanza y la independencia de $Z$ con respecto a $X_1$ y $X_2$:

$$\mathbb{E}[X] = \mathbb{E}[Z X_1] + \mathbb{E}[(1 - Z) X_2]$$

Como $Z$ es independiente de $X_1$ y de $X_2$:


$$\mathbb{E}[X] = \mathbb{E}[Z]\mathbb{E}[X_1] + \mathbb{E}[1 - Z]\mathbb{E}[X_2]$$

Sabiendo que $Z \sim \text{Ber}(\pi)$, tenemos $\mathbb{E}[Z] = \pi$ y $\mathbb{E}[1 - Z] = 1 - \pi$:


$$\mathbb{E}[X] = \pi \mu_1 + (1 - \pi)\mu_2$$

Sustituyendo los valores dados ($\mu_1 = 0$, $\mu_2 = 1$, $\pi = 1/4$):


$$\mathbb{E}[X] = \left(\frac{1}{4}\right)(0) + \left(1 - \frac{1}{4}\right)(1) = \frac{3}{4} = 0.75$$

* **$\mathbb{E}[X] =$** **`3/4`** (o **`0.75`**)

---

### 2. Varianza de $X$ ($\text{Var}(X)$)

Podemos utilizar la ley de varianza total condicionando sobre $Z$:


$$\text{Var}(X) = \mathbb{E}[\text{Var}(X \mid Z)] + \text{Var}(\mathbb{E}[X \mid Z])$$

* **Primer término ($\mathbb{E}[\text{Var}(X \mid Z)]$):**
* Si $Z = 1$, $X = X_1$, luego $\text{Var}(X \mid Z=1) = \sigma_1^2 = 1$.


* Si $Z = 0$, $X = X_2$, luego $\text{Var}(X \mid Z=0) = \sigma_2^2 = 1$.


* Como la varianza condicional es $1$ en ambos casos:

$$\mathbb{E}[\text{Var}(X \mid Z)] = 1$$




* **Segundo término ($\text{Var}(\mathbb{E}[X \mid Z])$):**
* Si $Z = 1$, $\mathbb{E}[X \mid Z=1] = \mu_1 = 0$.


* Si $Z = 0$, $\mathbb{E}[X \mid Z=0] = \mu_2 = 1$.


* Por tanto, $\mathbb{E}[X \mid Z] = 1 - Z$.
* La varianza de una variable Bernoulli es:

$$\text{Var}(\mathbb{E}[X \mid Z]) = \text{Var}(1 - Z) = \text{Var}(Z) = \pi(1 - \pi)$$


$$\text{Var}(\mathbb{E}[X \mid Z]) = \left(\frac{1}{4}\right)\left(\frac{3}{4}\right) = \frac{3}{16}$$





Sumando ambos términos:


$$\text{Var}(X) = 1 + \frac{3}{16} = \frac{19}{16} = 1.1875$$

* **$\text{Var}(X) =$** **`19/16`** (o **`1.1875`**)

---

### 3. ¿Es necesario asumir que $X_1$ es independiente de $X_2$?

Al calcular el segundo momento directamente:


$$X^2 = (Z X_1 + (1 - Z) X_2)^2 = Z^2 X_1^2 + 2 Z(1 - Z) X_1 X_2 + (1 - Z)^2 X_2^2$$

Dado que $Z \in \{0, 1\}$, se cumple que $Z^2 = Z$, $(1 - Z)^2 = 1 - Z$ y el término cruzado es siempre cero:


$$Z(1 - Z) = 0$$

Por lo tanto:


$$X^2 = Z X_1^2 + (1 - Z) X_2^2$$

El término que involucra el producto $X_1 X_2$ desaparece por completo, por lo que nunca se necesita la covarianza entre $X_1$ y $X_2$. Solo se requiere que $Z$ sea independiente de $X_1$ y de $X_2$.

* **Respuesta:** **`No`** 


---

## 2. Moment Generating Function

For a Gaussian \(X_i\sim N(\mu_i,\sigma_i^2)\),

$$
M_{X_i}(t)=e^{\mu_i t+\frac12\sigma_i^2t^2}.
$$

The mixture MGF is

$$
M_X(t)
=\frac14 e^{0t+\frac12t^2}
+\frac34 e^{1t+\frac12t^2}.
$$

At \(t=-1\):

$$
M_X(-1)
=\frac14e^{1/2}+\frac34e^{-1/2}.
$$

So enter:

$$
\boxed{\frac14e^{1/2}+\frac34e^{-1/2}}
$$

Equivalent form:

$$
\boxed{\frac{e+3}{4\sqrt e}}
$$

---

## 3. Parametric vs. Nonparametric Models

A model is **parametric** if its distributions can be specified using a finite number of parameters.

Go through the choices:

1. **All probability distributions on \(\{0,1,2,\ldots\}\)**
   ❌ **Nonparametric**

2. **Bernoulli(\(\theta\)), \(\theta\in[0,1]\)**
   ✅ **Parametric**

3. **\(N(0,\sigma^2)\), \(\sigma^2>0\)**
   ✅ **Parametric**

4. **Distribution on \(\{1,2,3,4\}\) with probabilities \(p_1,\ldots,p_4\)**
   ✅ **Parametric**
   There are only finitely many parameters.

5. **\(N(\mu,\sigma^2)\), \(\mu\in\mathbb R,\sigma^2>0\)**
   ✅ **Parametric**

6. **Uniform \([0,\theta]\), \(\theta>0\)**
   ✅ **Parametric**

7. **All distributions having an arbitrary continuous density on \([0,1]\)**
   ❌ **Nonparametric**

### Therefore, check:

$$
\boxed{2,\ 3,\ 4,\ 5,\ 6}
$$

--- 

Here are the answers:

### 1. Preparation: Injectivity

Check:

* \(f_1(x)=x\): **Yes** ✅
* \(f_2(x)=x^2\): **No** ❌ because \(f_2(1)=f_2(-1)\)
* \(f_3(x)=\sin x\): **No** ❌ because sine is periodic
* \(f_4(p)=\operatorname{Ber}(p)\): **Yes** ✅ because different \(p\)'s give different Bernoulli distributions.

**Select: \(\boxed{f_1,\ f_4}\)**

---

### 2. Identifiability of Statistical Models

#### A. \(\{\operatorname{Ber}(p)\}_{p\in[0,1]}\)

Different \(p\)'s give different Bernoulli distributions.

✅ **Identifiable**

#### B. \(\{\operatorname{Ber}(p^2)\}_{p\in[-1,1]}\)

For example,

$$
(-1)^2=1^2,
$$

so \(p=-1\) and \(p=1\) give the same distribution.

❌ **Not identifiable**

#### C. \(\{\operatorname{Ber}(\sin p)\}_{p\in[0,\pi/2]}\)

\(\sin p\) is strictly increasing on \([0,\pi/2]\).

✅ **Identifiable**

#### D. \(\{\operatorname{Ber}(\sin p)\}_{p\in[0,\pi]}\)

$$
\sin(p)=\sin(\pi-p),
$$

so different parameters can give the same distribution.

❌ **Not identifiable**

**Select:**

$$
\boxed{1\text{ and }3}
$$

---

### 3. Identifiability of Statistical Models 2

You have

$$
X_i=Y_i^2,\qquad Y_i\sim U([0,a]).
$$

Since

$$
0\le Y_i\le a,
$$

we get

$$
0\le X_i\le a^2.
$$

Thus the distribution of \(X_i\) has support ending at \(a^2\). From the distribution of \(X_i\), we can recover \(a\):

$$
a=\sqrt{\text{upper endpoint of the support}}.
$$

Therefore \(a\) is identifiable.

✅ **Select: Yes**

---

### 4. Identifiability of Statistical Models 3

$$
X_i=\mathcal I(Y_i\ge a/2),
\qquad Y_i\sim U([0,a]).
$$

Because \(Y_i\) is uniform on \([0,a]\),

$$
P(Y_i\ge a/2)=\frac{a-a/2}{a}=\frac12.
$$

Therefore,

$$
X_i\sim \operatorname{Ber}\left(\frac12\right),
$$

**regardless of the value of \(a\)**.

So the distribution of \(X_i\) contains no information that distinguishes different \(a\)'s.

❌ **Select: No**


