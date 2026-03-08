# SoftMax as probabilities relative to the largest logit

The common implementation of SoftMax reveals a nice mental model for thinking about SoftMax in deep neural networks.

Let's start with the mathematical definition of SoftMax is:

For logits $z_1, z_2, ..., z_n$:

$$
\text{softmax}(z_i) = \frac{e^{z_i}}{\sum_{j=1}^{n} e^{z_j}}
$$

The beauty of this function is that it wrangles the unbounded logits from $[-\infty, \infty]$ into neat little probabilities in the range $[0, 1]$ with only two steps. First, the exponential function, $e^z$, moves the values into $[0, \infty]$, then the each value is simply normalized.

Implementing this directly can cause overflow since $e^{z_i}$ grows **extremely fast**.  Common frameworks like PyTorch handle this by subtracting the max logit like so:

```
exp_logits = np.exp(logits - np.max(logits))
softmax = exp_logits / exp_logits.sum()
```

It's OK to subtract a constant value from each logit because **SoftMax is shift invariant** (proof below). **Subtracting the max logit guarantees numerical stability** since the exponential of the max is equal to one $e^{z_{max} - z_{max}} = e^0 = 1$ and all others are in the range $0 < e^{z_i - z_{max}} \le 1$. This makes overflow impossible.

$0 < e^{z_i - z_{max}} \le 1$

This numerical stability trick reveals a deeper insight about SoftMax: its all about the relative probabilities

Each probability depends only on:

$z_i - m$

which is **how far a logit is from the winner**.

# SoftMax Shift Invariance proof

If you subtract the same constant $c$ from every logit:

$\frac{e^{z_i}}{\sum_j e^{z_j}} = \frac{e^{z_i - c}}{\sum_j e^{z_j - c}}$
  
Proof:

$e^{z_i-c} = \frac{e^{z_i}}{e^c}$
  
$\sum_j e^{z_j-c} = \frac{1}{e^c}\sum_j e^{z_j}$
  
So:
$\frac{e^{z_i-c}}{\sum_j e^{z_j-c}} = \frac{e^{z_i}/e^c}{(\sum_j e^{z_j})/e^c} = \frac{e^{z_i}}{\sum_j e^{z_j}}$

The constant cancels out. Thus we can subtract **any constant** without changing softmax.

# **Softmax is really computing probabilities relative to the largest logit**

$0 < e^{z_i - z_{max}} \le 1$