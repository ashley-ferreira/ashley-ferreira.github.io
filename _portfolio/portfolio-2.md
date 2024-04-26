---
title: "ML-PSF: Tool to Pick Good Sources for PSF Generation"
excerpt: "<img src='../images/ml_psf_method2.png' style='max-width: 50%; display: inline-block;'>"
collection: portfolio
---

## TL;DR

We can maybe use machine learning to help pick stars for Point Spread Function creation to save time in the data processing pipeline. 

## Built With

[![Python][python]][python-url]
[![Notebook][notebook]][notebook-url] 
[![Keras][keras]][keras-url]
[![TensorFlow][tensorflow]][tensorflow-url]

[python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[python-url]: https://www.python.org/

[notebook]: https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter
[notebook-url]: https://jupyter.org/

[keras]: https://img.shields.io/badge/Keras-%23D00000.svg?style=for-the-badge&logo=Keras&logoColor=white
[keras-url]: https://keras.io/

[tensorflow]: https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white
[tensorflow-url]: https://www.tensorflow.org/


## Background

### What is a Point Spread Function (PSF)?
PSFs mathematically describe how point source objects are distorted in an image. Images are a convolution between the true object and its PSF.

### Why are PSFs important to astronomy?
PSFs are necessary to study any object close to the resolution limit of a telescope with high precision.

### What do we need in order to create PSFs?
Examples of point-like sources in the image of interest are needed as inputs to PSF generation software. In astronomy, good point-like sources would be stars that are
bright, round, and well isolated from other sources. The task of selecting these good sources for PSF generation is
what this deep learning model has been trained to do. 

## Goal

Given cutout of each source in an image along with their respective x and y coordinates, this program calls on a pre-trained machine learnining model that will return a subset of cutouts of sources to use for point spread function (PSF) creation. It also returns the x and y coordinates of these sources that can be used to pass into the python module TRIPPy in order to create the desired PSF. 

## Method

For this project, images from 2020 taken by the Hyper SuprimeCam (HSC). For each image, the top 25 sources were selected as those with
the lowest flux outside the central source, as inferred by the flux
of the most discrepant pixel in the source-PSF residual, and the
standard deviation of all residual pixels.
Of these top 25, the ones which fell in the accepted range of
pixel brightness values were deemed good and labelled 1. All
other sources were considered bad and labelled 0.
Using this approach, there are far more bad sources than good
ones and so a random selection of bad sources is made such
that the 0 and 1 class sizes are equal.


<img src="../../images/ml_psf_method1.png" alt="Image 5" style="max-width: 90%; display: inline-block;">

A simple 2D Convolutional Neural Network (CNN) was developed for
this binary classification problem:

<img src="../../images/ml_psf_method2.png" alt="Image 6" style="max-width: 90%; display: inline-block;">

## Results

The accuracy on the test set was found to be 89.12% overall. 

We can raise the confidence threshold beyond which the model
labels a source as good. A threshold of 90% was adopted such that
we can achieve a precision of 93.87% while still having a significant
number of sources classified as good:

<img src="../../images/ml_psf_results1.png" alt="Image 6" style="max-width: 60%; display: inline-block;">

Once the model is trained, the CNN method takes only ~6% the
CPU time of the non-CNN method:
<img src="../../images/ml_psf_results2.png" alt="Image 6" style="max-width: 90%; display: inline-block;">


## Conclusion 

Makes the PSF's faster but not nessisarily better. Some form of unsupervised learning is likely needed as a next step.

## Code

Publically available on GitHub: [github.com/ashley-ferreira/ML-PSF/](https://github.com/ashley-ferreira/ML-PSF/)