---
layout: post
title: Deep Learning 覚書
tags: [deep,learning]
---

個人的な Deep Learning の覚え書き。

## ニューラルネットワーク

- 何層かのニューロンで構成される。
  - ニューロンの式: $$ f \left wx+b \right $$

```math
f \left( wx+b \right)
```

$2^3$

```math
\left( \sum_{k=1}^n a_k b_k \right)^{!!2} \leq
\left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
```

$$
\begin{align*}
\frac{\partial \theta}{\partial t}= \frac{\partial}{\partial z}
\left[ K(\theta) \left (\frac{\partial \psi}{\partial z} + 1 \right) \right]\
\end{align*}
$$

半径 $$ r $$ の円の面積は $$ \pi r^2 $$ であり、球の体積は $$ \frac{4}{3}\pi r^3  $$ である。
