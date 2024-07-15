[![Build Status](https://travis-ci.com/felixriese/CNN-SoilTextureClassification.svg?branch=master)](https://travis-ci.com/felixriese/CNN-SoilTextureClassification)
[![codecov](https://codecov.io/gh/felixriese/CNN-SoilTextureClassification/branch/master/graph/badge.svg)](https://codecov.io/gh/felixriese/CNN-SoilTextureClassification)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/01c84806115646eb9ba2dde39a84822e)](https://www.codacy.com/manual/felixriese/CNN-SoilTextureClassification?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=felixriese/CNN-SoilTextureClassification&amp;utm_campaign=Badge_Grade)
[![Paper](https://img.shields.io/badge/DOI-10.5194%2Fisprs--annals--IV--2--W5--615--2019-blue)](https://www.isprs-ann-photogramm-remote-sens-spatial-inf-sci.net/IV-2-W5/615/2019/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

# CNN Soil Texture Classification

1-dimensional convolutional neural networks (CNN) for the classification of
soil texture based on hyperspectral data.

## Description

We present 1-dimensional (1D) convolutional neural networks (CNN) for the
classification of soil texture based on hyperspectral data. The following CNN
models are included:

* `LucasCNN`
* `LucasResNet`
* `LucasCoordConv`
* `HuEtAl`: 1D CNN by Hu et al. (2015), DOI: [10.1155/2015/258619](http://dx.doi.org/10.1155/2015/258619)
* `LiuEtAl`: 1D CNN by Liu et al. (2018), DOI: [10.3390/s18093169](https://dx.doi.org/10.3390%2Fs18093169)

These 1D CNNs are optimized for the soil texture classification based on the hyperspectral data of the *Land Use/Cover Area Frame Survey* (LUCAS) topsoil dataset. It is available [here](https://esdac.jrc.ec.europa.eu/projects/lucas). For more information have a look in our publication (see below).

## Requirements

* see [Dockerfile](Dockerfile)
* download `coord.py` from [titu1994/keras-coordconv](https://github.com/titu1994/keras-coordconv) based on [arXiv:1807.03247](https://arxiv.org/abs/1807.03247)

## Setup

```bash
git clone https://github.com/felixriese/CNN-SoilTextureClassification.git

cd CNN-SoilTextureClassification/

wget https://raw.githubusercontent.com/titu1994/keras-coordconv/c045e3f1ff7dabd4060f515e4b900263eddf1723/coord.py .
```

## Usage

You can import the Keras models like that:

```python
import cnn_models as cnn

model = cnn.getKerasModel("LucasCNN")
model.compile(...)

```

Example code is given in the `lucas_classification.py`. You can use it like that:

```python
from lucas_classification import lucas_classification

score = lucas_classification(
    data=[X_train, X_val, y_train, y_val],
    model_name="LucasCNN",
    batch_size=32,
    epochs=200,
    random_state=42)

print(score)
```
