---
layout: post
title: Deep Learning 覚書
tags: [deep,learning]
modified: 2019-03-17
---

個人的な Deep Learning の覚え書き。

## 必要な数学の知識

### 記号

* δ(デルタ): 微小正数を表す。
* ⊿(デルタ): 差分や微小増分を表す。
* d(ディー): 常微分。
* ∂(ラウンド・ディー): 偏微分。幾何学では領域の境界を表す。
* ∇(ナブラ): 偏微分ベクトル。

### 偏微分

複数の変数がある関数で、1つの変数のみ微分することを、偏微分と言う。

例えば $$ f(a, b, c) = a^2 + b^2 + c^2 + 1 $$ として、$$ f $$ の $$ a $$ に関する偏微分は $$ \frac {\partial f}{\partial a} = 2a $$ 。

$$ a $$ 以外の変数はすべて定数と見なすので、$$ a $$ を含まない項は消える。

微分の記号は $$ d $$ の代わりに $$ \partial $$ を使う。

### 合成関数の偏微分公式

$$ a $$ が $$ b_1, b_2, \dots, b_n $$ の関数（複数変数を持つ）で、$$ b_1, b_2, \dots, b_n $$ がそれぞれ $$ c $$ の関数である場合、 $$ a $$ を $$ c $$ で偏微分すると下記のようになる。

$$ [\frac {\partial a}{\partial c} = \sum_{k=1}^n \frac {\partial a}{\partial b_k} \frac {\partial b_k}{\partial c}] $$

## 逆伝播の考え方

$$ δLj=∂C∂aLjσ′(zLj) $$

$$ δl=((wl+1)Tδl+1)⊙σ′(zl) $$

$$ ∂C∂blj=δlj $$

$$ ∂C∂wljk=al−1kδlj $$

## ニューラルネットワーク

- 何層かのニューロンで構成される。
  - ニューロンの式: $$ y = f \left( wx + b \right) $$
    - $$ y $$ は出力、$$ f $$ は活性化関数、$$ w $$ は重み、$$ b $$ はバイアス。
  - 活性化関数
    - シグモイド関数: $$ \sigma(z) \equiv \frac{1}{1+e^{-z}} $$

## 全結合層

### 順伝播

- 前層 In:x → Fully connected layer → Out:y 後続層
  - $$ y $$ は出力、$$ f $$ は活性化関数、$$ w $$ は重み、$$ b $$ はバイアス。

$$ y = f \left( wx + b \right) $$

- 活性化関数
  - シグモイド関数: $$ \sigma(z) \equiv \frac{1}{1+e^{-z}} $$

### 逆伝播

- 前層 dIn ← Fully connected layer ← dOut 後続層

$$ dIn = {}^t\!Weight * dOut $$

### 重みの更新

$$ dW = {}^t\!In * dOut $$

## Convolution(畳み込み層)

### 順伝播

- 前層 In → Convolution → Out 後続層

$$ Out = Weight * In $$

### 逆伝播

- 前層 dIn ← Convolution ← dOut 後続層

$$ dIn = {}^t\!Weight * dOut $$

### 重みの更新

$$ dW = {}^t\!In * dOut $$

dB は Channel 毎の dOut の総和

## YOLO9000

- 顔認識

```bash
wget https://modeldepot.io/assets/uploads/models/models/2ab9c908-15c0-438d-905e-e75363c52c72_azFace.zip -O azFace.zip
```

- [https://timebutt.github.io/static/how-to-train-yolov2-to-detect-custom-objects/](https://timebutt.github.io/static/how-to-train-yolov2-to-detect-custom-objects/)

## データセット

- [http://www.robots.ox.ac.uk/~vgg/data/](http://www.robots.ox.ac.uk/~vgg/data/)
- [https://caffe2.ai/docs/datasets.html](https://caffe2.ai/docs/datasets.html)
- 顔: [https://data.vision.ee.ethz.ch/cvl/rrothe/imdb-wiki/](https://data.vision.ee.ethz.ch/cvl/rrothe/imdb-wiki/)
  - Wikiの顔画像に対して生年月日と撮影日が記載されたデータセット。Download Faces Onlyで7GB。460723枚。ラベルはMatlab形式。
- 顔: [https://talhassner.github.io/home/projects/Adience/Adience-data.html#agegender](https://talhassner.github.io/home/projects/Adience/Adience-data.html#agegender)
  - 年齢と性別が記載されたデータセット。1.76GB。11524枚。
  - 登録が必要。
- 顔: [http://vis-www.cs.umass.edu/fddb/](http://vis-www.cs.umass.edu/fddb/)
  - 顔の位置が記載されたデータセット。75MB。2845枚。
- 顔: [http://mmlab.ie.cuhk.edu.hk/projects/WIDERFace/](http://mmlab.ie.cuhk.edu.hk/projects/WIDERFace/)
  - 顔の位置が記載されたデータセット。1.56GB。12880枚。
- 犬: [http://vision.stanford.edu/aditya86/ImageNetDogs/](http://vision.stanford.edu/aditya86/ImageNetDogs/)
- 鳥: [http://www.vision.caltech.edu/visipedia/CUB-200.html](http://www.vision.caltech.edu/visipedia/CUB-200.html)

$$
\begin{align*}
\frac{\partial \theta}{\partial t}= \frac{\partial}{\partial z}
\left[ K(\theta) \left (\frac{\partial \psi}{\partial z} + 1 \right) \right]\
\end{align*}
$$

半径 $$ r $$ の円の面積は $$ \pi r^2 $$ であり、球の体積は $$ \frac{4}{3}\pi r^3  $$ である。
