## 1. Which statistics are estimators?

An **estimator must be a function of the observed data** \(X_1,\ldots,X_n\). It cannot depend on the unknown parameter \(\theta\).

Check the options:

* \(\theta\) ❌ — unknown parameter, not a statistic.
* \(4.2\) ✅ — a constant is a statistic (it doesn't depend on unknown quantities).
* \(\displaystyle\sum_{i=1}^n i^2X_i\) ✅ — depends only on the data.
* \(\displaystyle\frac1n\sum_{i=1}^nX_i\) ✅ — the sample mean.
* \(\displaystyle\frac1n\sum_{i=1}^nX_i-\theta\) ❌ — depends on the unknown \(\theta\).

### Select:

$$
\boxed{4.2,\quad \sum_{i=1}^n i^2X_i,\quad \frac1n\sum_{i=1}^nX_i}
$$

---

## 2. Consistency of an estimator

Here \(\theta\) is the common mean:

$$
E[X_i]=\theta.
$$

Check each:

* \(\theta\) ❌ — not an estimator, as established above.
* \(4.2\) ❌ — since \(\theta\ne4.2\), it converges to \(4.2\), not \(\theta\).
* \(\displaystyle\sum_{i=1}^n i^2X_i\) ❌ — does not converge to the fixed value \(\theta\); it grows with \(n\).
* \(\displaystyle\frac1n\sum_{i=1}^nX_i\) ✅ — by the Law of Large Numbers,

  $$
  \frac1n\sum_{i=1}^nX_i\xrightarrow{P}\theta.
  $$
* \(\displaystyle\frac1n\sum_{i=1}^nX_i-\theta\) ❌ — this converges to \(0\), not \(\theta\).

### Select:

$$
\boxed{\frac1n\sum_{i=1}^nX_i}
$$

---

## 3. Quantifying Consistency

We have

$$
X_i\sim\operatorname{Ber}(p),
\qquad
\bar X_n=\frac1n\sum_{i=1}^nX_i.
$$

We want the critical value of \(c\) for

$$
n^c(\bar X_n-p).
$$

Since

$$
\operatorname{Var}(\bar X_n)
=\frac{p(1-p)}{n},
$$

the variance of the scaled quantity is

$$
\operatorname{Var}\left[n^c(\bar X_n-p)\right]
=
n^{2c}\frac{p(1-p)}{n}
=
p(1-p)n^{2c-1}.
$$

* If $c<\frac12$, the variance goes to \(0\), so the quantity converges to \(0\) in probability.
* At $c=\frac12$, the variance stays at \(p(1-p)\), and by the CLT the quantity has a non-degenerate limiting distribution, so it **does not** converge to \(0\) in probability.
* For $c>\frac12$, it also does not converge to \(0\).

Thus the **critical/smallest value** is

$$
\boxed{\frac12}.
$$

---

Sure — all three are straightforward.

### 4. The Expectation of the Average

$$
X_i\overset{iid}{\sim}U([a,a+1])
$$

For a uniform distribution \(U([a,b])\),

$$
E[X_i]=\frac{a+b}{2}.
$$

Here \(b=a+1\), so

$$
E[X_i]=\frac{a+(a+1)}2=a+\frac12.
$$

Since the expectation of the sample mean equals the population mean,

$$
E[\bar X_n]=a+\frac12.
$$

**Enter:**

$$
\boxed{a+\frac12}
$$

---

### 5. Computing Bias

Bias is

$$
\operatorname{Bias}(\bar X_n)
=E[\bar X_n]-a.
$$

From above,

$$
E[\bar X_n]=a+\frac12.
$$

Therefore,

$$
\operatorname{Bias}(\bar X_n)
=a+\frac12-a
=\frac12.
$$

**Enter:**

$$
\boxed{\frac12}
$$
---
### 6\. Unbiased estimators — select:

 - ✅ $\bar X_n$
- ✅ $X_2$
- ❌ $\mathbb E[\bar X_n]$
- ❌ $\frac1{\sqrt n}\sum_{i=1}^n X_i$
- ❌ $\frac{\sqrt n\,\bar X_n}{\sigma}$
- ✅ $\frac{2}{n(n+1)}\sum_{i=1}^n iX_i$

 ### 7\. Quadratic risk

 For $X_i\sim U([a,a+1])$,\

$$
E[X_i]=a+\frac12,\qquad \operatorname{Var}(X_i)=\frac1{12}.
$$

\
 Thus $\bar X_n-\frac12$ is unbiased for $a$, so\

$$
\boxed{R=\frac{1}{12n}}.
$$
---

### 8. Variance of the Sample Mean

For \(X_i\sim U([a,a+1])\), the interval has length \(1\).

The variance of \(U([a,b])\) is

$$
\operatorname{Var}(X_i)=\frac{(b-a)^2}{12}.
$$

Thus

$$
\operatorname{Var}(X_i)=\frac{1^2}{12}=\frac1{12}.
$$

For the sample mean,

$$
\operatorname{Var}(\bar X_n)
=\frac{\operatorname{Var}(X_i)}{n}
=\frac{1}{12n}.
$$

**Enter:**

$$
\boxed{\frac{1}{12n}}
$$

---
 ### 9\. Properties ensuring convergence in probability

 Select:

 - ✅ $\hat\theta_n$ is consistent.
- ❌ $\hat\theta_n$ is unbiased.
- ✅ Quadratic risk goes to $0$.
- ❌ Variance goes to $0$.

---

### 10: $\hat\theta_n=0.5$

 Select:

 - ✅ Unless $\theta=.5$, this estimator is biased.
- ✅ Unless $\theta=.5$, this estimator is not consistent.
- ✅ This estimator does not use any of the samples.
- ❌ Efficiently computable.

 ### 11: $\hat\theta_n=X_1$

 Select:

 - ❌ Unbiased.
- ✅ This estimator is not consistent.
- ✅ Uses only one sample.
- ✅ Quadratic risk does not tend to $0$.

 ### 12: $\hat\theta_n=\bar X_n$

 Select **all four**:

 - ✅ Unbiased.
- ✅ Consistent.
- ✅ Efficiently computable.
- ✅ Quadratic risk tends to $0$ as $n\to\infty$.

--- 

### 1. Random or Deterministic?

| Quantity         | Answer              |
| ---------------- | ------------------- |
| \(\bar R_n\)     | ✅ **random**        |
| \(n\)            | ✅ **deterministic** |
| \(q_{\alpha/2}\) | ✅ **deterministic** |
| \(p\)            | ✅ **deterministic** |

**Why:** \(\bar R_n\) depends on the random observations \(R_1,\ldots,R_n\). The sample size \(n\), quantile \(q_{\alpha/2}\), and parameter \(p\) are fixed quantities (even though \(p\) is unknown).

---

### 2. Conservative bound

We have

$$
\sigma_p=\sqrt{p(1-p)}.
$$

To replace \(\sigma_p\) with \(c\) and **guarantee the confidence level for every \(p\in(0,1)\)**, we need

$$
c\geq \sigma_p \qquad \text{for all }p.
$$

Therefore, select:

* ✅ **\(c\geq \sigma_p\) for all \(p\)**
* ❌ \(c\geq\sigma_p\) for some \(p\)
* ✅ **\(c=\max_p(\sigma_p)\)**
* ❌ \(c\leq\sigma_p\) for all \(p\)
* ❌ \(c\leq\sigma_p\) for some \(p\)
* ❌ \(c=\min_p(\sigma_p)\)

In fact,

$$
\max_{0<p<1}\sqrt{p(1-p)}=\frac12
$$

at \(p=\frac12\), so the usual conservative choice is

$$
\boxed{c=\frac12}.
$$

### Final selections

**Question 1:**
**random, deterministic, deterministic, deterministic**

**Question 2:**
**\(c\geq\sigma_p\) for all \(p\)** and **\(c=\max_p(\sigma_p)\)**.

For this confidence-bound question

* Derive the conservative interval
* Explain why c = 1/2 works
----

There are **two parts**.

### 1. Correct quadratic inequality

Start with

$$
\sqrt n\frac{|\bar R_n-p|}{\sqrt{p(1-p)}}<q_{\alpha/2}.
$$

Square both sides:

$$
n(\bar R_n-p)^2<q_{\alpha/2}^2p(1-p).
$$

Expand:

$$
n(\bar R_n^2-2\bar R_np+p^2)
<q_{\alpha/2}^2p-q_{\alpha/2}^2p^2.
$$

Move everything to the left:

$$
(n+q_{\alpha/2}^2)p^2
-(2n\bar R_n+q_{\alpha/2}^2)p
+n\bar R_n^2<0.
$$

So the correct choice is:

$$
\boxed{Ap^2+Bp+C<0\quad\text{where }A>0.}
$$

✅ **Select the FIRST option.**

---

### 2. Where is the quadratic negative?

For a quadratic with \(A>0\) and two roots

$$
p_1<p_2,
$$

the parabola opens **upward**, so it is negative **between the two roots**:

$$
\boxed{p_1<p<p_2}.
$$

✅ **Select the SECOND option.**

### Final answers

1. **\(Ap^2+Bp+C<0\) where \(A>0\)**
2. **\(p_1<p<p_2\)**

Continue with the confidence interval

* Derive the quadratic roots
* Compare with the c = 1/2 bound


----


Para encontrar los valores numéricos de $A$, $B$ y $C$, y el correspondiente intervalo de confianza para $p$, partimos de la desigualdad cuadrática obtenida al despejar $p$:

$$\left\vert{} \sqrt{n} \frac{\overline{R}_n - p}{\sqrt{p(1-p)}} \right\vert{} < q_{\alpha/2}$$

Elevando ambos lados al cuadrado:


$$n \frac{(\overline{R}_n - p)^2}{p(1-p)} < q_{\alpha/2}^2$$

Multiplicando por $p(1-p) > 0$:


$$n (\overline{R}_n - p)^2 < q_{\alpha/2}^2 p(1-p)$$

Dividiendo entre $n$:


$$(\overline{R}_n - p)^2 < \frac{q_{\alpha/2}^2}{n} (p - p^2)$$

Desarrollando el binomio $(\overline{R}_n - p)^2 = p^2 - 2\overline{R}_n p + \overline{R}_n^2$:


$$p^2 - 2\overline{R}_n p + \overline{R}_n^2 < \frac{q_{\alpha/2}^2}{n} p - \frac{q_{\alpha/2}^2}{n} p^2$$

Reagrupando todos los términos del lado izquierdo en la forma $A p^2 + B p + C < 0$:


$$\left(1 + \frac{q_{\alpha/2}^2}{n}\right) p^2 - \left(2\overline{R}_n + \frac{q_{\alpha/2}^2}{n}\right) p + \overline{R}_n^2 < 0$$

Notemos que el término independiente es exactamente $C = (\overline{R}_n)^2$, tal como especifica la indicación del problema.

---

### 1. Cálculo de los coeficientes $A$, $B$ y $C$

Datos dados:

* $n = 100$

* $\overline{R}_n = 0.645$

* Nivel de confianza asintótico del $95\%$ ($\alpha = 0.05 \implies q_{\alpha/2} = 1.96$)



Calculamos el término común:


$$\frac{q_{\alpha/2}^2}{n} = \frac{(1.96)^2}{100} = \frac{3.8416}{100} = 0.038416$$

* **Valor de $A$:**

$$A = 1 + \frac{q_{\alpha/2}^2}{n} = 1 + 0.038416 = 1.038416 \approx \mathbf{1.0384}$$


* **Valor de $B$:**

$$B = -\left(2\overline{R}_n + \frac{q_{\alpha/2}^2}{n}\right) = -(2 \cdot 0.645 + 0.038416) = -(1.29 + 0.038416) = -1.328416 \approx \mathbf{-1.3284}$$


* **Valor de $C$:**

$$C = (\overline{R}_n)^2 = (0.645)^2 = 0.416025 \approx \mathbf{0.4160}$$



---

### 2. Intervalo de confianza para $p$ ($\mathcal{I}_{\text{solve}}$)

Las raíces del polinomio $A p^2 + B p + C = 0$ con los coeficientes redondeados a 4 decimales:


$$p = \frac{-B \pm \sqrt{B^2 - 4AC}}{2A}$$

1. **Discriminante:**

$$\Delta = B^2 - 4AC = (-1.3284)^2 - 4(1.0384)(0.4160)$$


$$\Delta = 1.76464656 - 1.72790016 = 0.0367464$$


$$\sqrt{\Delta} \approx 0.1916935$$


2. **Límite inferior:**

$$p_{\min} = \frac{1.3284 - 0.1916935}{2(1.0384)} = \frac{1.1367065}{2.0768} \approx 0.5473 \approx \mathbf{0.55}$$


3. **Límite superior:**

$$p_{\max} = \frac{1.3284 + 0.1916935}{2(1.0384)} = \frac{1.5200935}{2.0768} \approx 0.7319 \approx \mathbf{0.73}$$



---

### Respuestas para ingresar:

* $0 < A =$ **`1.0384`**
* $B =$ **`-1.3284`**
* $C =$ **`0.4160`** *(o `0.416`)*
* $p \in [\,$ **`0.55`** $\,,\,$ **`0.73`** $\, ]$

--- 

A continuación se detalla el análisis de las convergencias para cada una de las cantidades de ambas imágenes:

---

### Imagen 1: `Convergences of different quantities`

1. **Para $\overline{R}_n$**:


* Por la **Ley de los Grandes Números (LLN)**, el promedio muestral converge en probabilidad a la media poblacional:

$$\overline{R}_n \xrightarrow[n\to\infty]{(\mathbf{P})} p$$



* Por el **Teorema del Límite Central (TLC)**, la distribución de $\overline{R}_n$ tiene media $p$ y varianza $\frac{\text{Var}(R_1)}{n} = \frac{p(1-p)}{n}$, por lo que se aproxima en distribución por:

$$\mathcal{N}\left(p, \, \frac{p(1-p)}{n}\right)$$



* **Casillas a marcar:**
* **Fila 3:** `is approximated by (in distribution)` $\mathcal{N}\left(p, \frac{p(1-p)}{n}\right)$

* **Fila 5:** $\xrightarrow[n\to\infty]{(\mathbf{P})} p$





2. **Para $\sqrt{n}\left(\overline{R}_n - p\right)$**:


* Aplicando directamente el **Teorema del Límite Central**:

$$\sqrt{n}(\overline{R}_n - \mathbb{E}[R_1]) \xrightarrow[n\to\infty]{(d)} \mathcal{N}(0, \text{Var}(R_1)) = \mathcal{N}(0, p(1-p))$$



* **Casillas a marcar:**
* **Fila 2:** $\xrightarrow[n\to\infty]{(d)} \mathcal{N}(0, p(1-p))$





3. **Para $\sqrt{n}\frac{\overline{R}_n - p}{\sqrt{p(1-p)}}$**:


* Es la variable estandarizada por el TLC, por lo que converge en distribución a una normal estándar:

$$\sqrt{n}\frac{\overline{R}_n - p}{\sqrt{p(1-p)}} \xrightarrow[n\to\infty]{(d)} \mathcal{N}(0, 1)$$



* **Casillas a marcar:**
* **Fila 1:** $\xrightarrow[n\to\infty]{(d)} \mathcal{N}(0, 1)$






---

### Imagen 2: `Convergences of different quantities (continued)`

1. **Para $\sqrt{\overline{R}_n(1 - \overline{R}_n)}$**:


* Dado que $\overline{R}_n \xrightarrow{(\mathbf{P})} p$, por el **Teorema de la Función Continua** (mapping theorem):

$$\sqrt{\overline{R}_n(1 - \overline{R}_n)} \xrightarrow[n\to\infty]{(\mathbf{P})} \sqrt{p(1-p)}$$



* **Casillas a marcar:**
* **Fila 7 (última):** $\xrightarrow[n\to\infty]{(\mathbf{P})} \sqrt{p(1-p)}$





2. **Para $\frac{\sqrt{\overline{R}_n(1 - \overline{R}_n)}}{\sqrt{p(1-p)}}$**:


* Como el numerador converge en probabilidad a $\sqrt{p(1-p)}$ y el denominador es una constante no nula igual a $\sqrt{p(1-p)}$, el cociente converge en probabilidad a 1:

$$\frac{\sqrt{\overline{R}_n(1 - \overline{R}_n)}}{\sqrt{p(1-p)}} \xrightarrow[n\to\infty]{(\mathbf{P})} 1$$



* **Casillas a marcar:**
* **Fila 6:** $\xrightarrow[n\to\infty]{(\mathbf{P})} 1$





3. **Para $\left(\sqrt{n}\frac{\overline{R}_n - p}{\sqrt{p(1-p)}}\right)\left(\frac{\sqrt{p(1-p)}}{\sqrt{\overline{R}_n(1-\overline{R}_n)}}\right)$**:


* Esta expresión es equivalente a $\sqrt{n}\frac{\overline{R}_n - p}{\sqrt{\overline{R}_n(1-\overline{R}_n)}}$ (el pivote de Student/Slutsky).


* Por el **Lema de Slutsky**: el primer término converge en distribución a $\mathcal{N}(0,1)$ y el segundo converge en probabilidad a $1$.


* Por tanto, el producto converge en distribución a $\mathcal{N}(0, 1) \cdot 1 = \mathcal{N}(0, 1)$:

$$\xrightarrow[n\to\infty]{(d)} \mathcal{N}(0, 1)$$



* **Casillas a marcar:**
* **Fila 1:** $\xrightarrow[n\to\infty]{(d)} \mathcal{N}(0, 1)$


