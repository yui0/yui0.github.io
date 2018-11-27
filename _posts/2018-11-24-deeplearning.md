---
layout: post
title: Deep Learning 覚書
tags: [deep,learning]
---

個人的な Deep Learning の覚え書き。

## ニューラルネットワーク

- 何層かのニューロンで構成される。
  - ニューロンの式: $$ f \left( wx + b \right) $$

## データセット

- [http://www.robots.ox.ac.uk/~vgg/data/](http://www.robots.ox.ac.uk/~vgg/data/)
- [https://data.vision.ee.ethz.ch/cvl/rrothe/imdb-wiki/](https://data.vision.ee.ethz.ch/cvl/rrothe/imdb-wiki/)
- [https://caffe2.ai/docs/datasets.html](https://caffe2.ai/docs/datasets.html)

$$
\begin{align*}
\frac{\partial \theta}{\partial t}= \frac{\partial}{\partial z}
\left[ K(\theta) \left (\frac{\partial \psi}{\partial z} + 1 \right) \right]\
\end{align*}
$$

半径 $$ r $$ の円の面積は $$ \pi r^2 $$ であり、球の体積は $$ \frac{4}{3}\pi r^3  $$ である。
