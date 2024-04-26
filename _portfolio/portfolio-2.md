---
title: "Lowering Uncertainties on Antimatter Gravity with Deep Learning"
excerpt: "<img src='../images/valid_compare.png' style='max-width: 60%; display: inline-block;'>"
collection: portfolio
tags:
- python
- pytorch
- multi-GPU
---

## Built With

[![Python][python]][python-url]
[![Notebook][notebook]][notebook-url] 
[![PyTorch][pytorch]][pytorch-url]
[![WandB][wandb]][wandb-url] 

[python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[python-url]: https://www.python.org/

[notebook]: https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter
[notebook-url]: https://jupyter.org/

[wandb]: https://img.shields.io/badge/Weights_&_Biases-FFBE00?style=for-the-badge&logo=WeightsAndBiases&logoColor=white
[wandb-url]: https://wandb.ai/site

[pytorch]: https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white
[pytorch-url]: https://pytorch.org/


## Goal

The goal of this project is to create a machine learning based model to predict the anihilation positions of antihydrogen for the ALPHA-g antimatter experiment at CERN.

First, we trained on real data, but then decided to train on instead simulations so currently all of this code is geared towards training on the simulations but it shouldn't be too hard to apply to real data again.

## Method

<img src="../../images/alpha_method.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

## Results

The results of this project are always slowly improving and below I outline the results you should get if you follow the quick start steps in the code provided. Note that further improvement can be made by training the model more after convergence of the loss but at a lower learning rate, and implimenting learning rate decay would be a more grown up way to approach this. 


### Loss 
Two straightforward choices for the loss function in a regression problem like this one is Mean Squared Error (MSE) or Mean Absolute Error (MAE). MAE is what I have been using for the most part. 

We see a relatively healthy loss curve during training, as shown in, where the loss converges for both the training and validation datasets as shown below:

<img src="../../images/MAE_overall.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

With the model's loss being mostly converged before epoch 200, below is a zoomed in plot of this early section:

<img src="../../images/MAE_atEpoch200.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

One thing that should stand out is that the validation loss is consistently lower than the training loss, and I'm pretty sure this is due to non-zero dropout being used as increasing dropout increases this effect and decreasing the dropout to zero makes the training loss drop to lower than the validation loss as would be expected. 

Note that this is on normalized data, with 0 being the bottom of the detector and 1 being the top. So in real terms a validation loss of 0.0065 means an unnormalized MAE of much larger value when in mm.

### Predictions
What is most interesting, is taking the unnormalized predictions and comparing them to the known real z values. There are two main plots we have been using to do this, with the first being a plot of predicted versus true z and shown below:

<img src="../../images/valid_compare.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

And a more granular way of analyzing this plot is by calculating the residuals and doing a guassian fit, which is shown below:

<img src="../../images/valid_residuals.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

The good news about this plot is it means in the majority of cases, the predicted z value of anihilation is within 15 mm of the real z position of anihilation.

Note that the mean is not consistent with zero in the latter plot and there is some clear z-bias in the former plot and these are features we do not want and that Yukiya has been able to create a model that not only has a smaller standard deviation but does not have these issues with the mean and z-bias.

The evaluation notebook also shows how to generate a similar residual analysis for the test set but we are hoping to not focus much on the test set since we know we can make the validation results better and are still tweaking the model. Ideally, a new test set is used from the additional simmulation data we have available to us so that it is never used until the very end. 


## Conclusion 

These results are very promissing and more peole have done work on this since, leading to even more promissing results.


## Code

Code is currently available through the internal TRIUMF GitLab and will hopefully be made publically available too:

<img src="../../images/gitlab.png" alt="Image 5" style="max-width: 100%; display: inline-block;">