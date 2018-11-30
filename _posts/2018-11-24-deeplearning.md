---
layout: post
title: Deep Learning 覚書
tags: [deep,learning]
modified: 2018-11-30
---

個人的な Deep Learning の覚え書き。

## ニューラルネットワーク

- 何層かのニューロンで構成される。
  - ニューロンの式: $$ f \left( wx + b \right) $$
  - 活性化
    - シグモイド関数: $$ \sigma(z) \equiv \frac{1}{1+e^{-z}} $$

## Convolution(畳み込み層)

### 順伝播

- 前層 In → Convolution → Out 後続層

$$ Out = Weight * In $$

### 逆伝播

- 前層 dIn ← Convolution ← dOut 後続層

$$ dIn = {}^t\!Weight * dOut $$

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
