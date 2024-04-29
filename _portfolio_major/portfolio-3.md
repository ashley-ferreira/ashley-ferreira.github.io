---
title: "Reconstructing Antimatter Events with Deep Learning"
excerpt: "<img src='../images/alpha_preview.png' style='max-width: 60%; display: inline-block;'>"
collection: portfolio_major
tags:
- python
- pytorch
- git
- computer vision
---

## TL;DR
Reconstructing antimatter events with Machine Learning (ML) is a relatively untouched approach and my work has shown it to be viable using simulations from the leading experiment located at CERN.

## Built With

[![Python][python]][python-url]
[![Notebook][notebook]][notebook-url] 
[![PyTorch][pytorch]][pytorch-url]
[![WandB][wandb]][wandb-url] 
[![vscode][vscode]][vscode-url]
[![gitlab][gitlab]][gitlab-url]

[gitlab]: https://img.shields.io/badge/gitlab-%23181717.svg?style=for-the-badge&logo=gitlab&logoColor=white
[gitlab-url]: https://about.gitlab.com/

[python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[python-url]: https://www.python.org/

[notebook]: https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter
[notebook-url]: https://jupyter.org/

[wandb]: https://img.shields.io/badge/Weights_&_Biases-FFBE00?style=for-the-badge&logo=WeightsAndBiases&logoColor=white
[wandb-url]: https://wandb.ai/site

[pytorch]: https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white
[pytorch-url]: https://pytorch.org/


[vscode]: https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white
[vscode-url]: https://code.visualstudio.com/

## Background
Antimatter is similar to normal matter but has the opposite charge and is much more rare. When a particle and its antiparticle meet, they annihilate, so the fact that the universe seems to be dominated by matter is not well understood since equal amounts of matter and antimatter are thought to have been produced during the Big Bang. Some of the most compelling theories to explain this suggest that matter and antimatter must react differently to a force like gravity. 

ALPHA is a leading experiment in the study of antimatter, with a track record of publishing [major breakthroughs](https://alpha.web.cern.ch/publications) in Nature. The most recent of which was [Observation of the effect of gravity on the motion of antimatter](https://www.nature.com/articles/s41586-023-06527-1) in September 2023 which detailed the first-ever measurements of the effect of gravity on antimatter, providing that it does fall down, and not up, but leaving large uncertatinties ranges that nessisitate antimatter be measured further before it can be said if gravity effects a particle and its antiparticle differently. 

## Goal

ML-based event reconstruction may be one way to lower these uncertainty bounds and so the goal of this project is to create a ML model that predicts the anihilation positions of antihydrogen for the ALPHA-g antimatter experiment at CERN.

Currently, the model is trained on simulations but the plan is to adapt it to real data in the future.

## Method
Method used is a fully-supervised implimentation of PointNet:
<img src="../../images/alpha_method.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

## Results

The results of this project are always slowly improving and below I outline the results you should get if you follow the quick start steps in the code provided. Note that further improvement can be made by training the model more after convergence of the loss but at a lower learning rate, and implimenting learning rate decay would be a more grown up way to approach this. 


### Mean Absolute Error Loss in Training

We see a relatively healthy loss curve during training, as shown in, where the loss converges for both the training and validation datasets as shown below:

<img src="../../images/MAE_overall.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

With the model's loss being mostly converged before epoch 200, below is a zoomed in plot of this early section:

<img src="../../images/MAE_atEpoch200.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

One thing that should stand out is that the validation loss is consistently lower than the training loss, and I'm pretty sure this is due dropout being used.

### Antimatter Position Predictions
What is most interesting, is taking the unnormalized predictions and comparing them to the known real z values. There are two main plots we have been using to do this, with the first being a plot of predicted versus true z and shown below:

<img src="../../images/valid_compare.png" alt="Image 5" style="max-width: 70%; display: inline-block;">

And a more granular way of analyzing this plot is by calculating the residuals and doing a guassian fit, which is shown below:

<img src="../../images/valid_residuals.png" alt="Image 5" style="max-width: 70%; display: inline-block;">

The good news about this plot is it means in the majority of cases, the predicted z value of anihilation is within 15 mm of the real z position of anihilation.

The bad news is that these results still lag behind the tradiaitonal computational method and so more work needs to be done for the ML method to beat and not just compliment, or backup, the traditional method. 


## Conclusion 

These results are very promissing and more peole have done work on this since, leading to even more promissing results like the reduction in standard deviation as well as bias in z. Keep your eye out for a paper about this!


## Code

Code is currently available through the internal TRIUMF GitLab and will hopefully be made publically available too:

<img src="../../images/gitlab.png" alt="Image 5" style="max-width: 100%; display: inline-block;">