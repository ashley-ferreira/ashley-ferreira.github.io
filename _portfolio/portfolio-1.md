---
title: "Reconstructing Antimatter Events with Deep Learning"
excerpt: "<img src='../images/alpha_preview.png' style='max-width: 60%; display: inline-block;'>"
collection: portfolio
tags:
- python
- pytorch
- git
- computer vision
---
## Status Update
This is super preliminary and in-progress work from the summer of 2023 and now that I am back on this project we have been able to dramatically increase the resolution and lower the z-dependant bias of the model such that it is beating the conventional method and has the potential to be used for real physics analysis. I will update this page towards the end of summer 2024 with the final results and hopefully details on a publication.

## TL;DR
Reconstructing antimatter events with Machine Learning (ML) is a relatively untouched approach and my work has shown it to be viable using simulations from the leading experiment located at CERN.

## Built With

[![Python][python]][python-url]
[![Notebook][notebook]][notebook-url] 
[![PyTorch][pytorch]][pytorch-url]
[![WandB][wandb]][wandb-url]
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

ALPHA is a leading experiment in the study of antimatter, with a track record of publishing [major breakthroughs](https://alpha.web.cern.ch/publications) in Nature. The most recent of which was [Observation of the effect of gravity on the motion of antimatter](https://www.nature.com/articles/s41586-023-06527-1) in September 2023 which detailed the first-ever measurements of the effect of gravity on antimatter, providing that it does fall down, and not up, but leaving large uncertainties ranges that necessitate antimatter be measured further before it can be said if gravity effects a particle and its antiparticle differently. 

## Goal

ML-based event reconstruction may be one way to lower these uncertainty bounds and so the goal of this project is to create a ML model that predicts the annihilation positions of antihydrogen for the ALPHA-g antimatter experiment at CERN.

Currently, the model is trained on simulations but the plan is to adapt it to real data in the future.

## Method
Method used is a fully-supervised implementation of PointNet:
<img src="../../images/alpha_method.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

And the goal is that this can replace the existing "Helix Fit" method:
<img src="../../images/alpha_helix.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

## Results
Our results are constantly improving these days but generally, we take the unnormalized predictions and comparing them to the known real z values. They are shown to have a really strong correlation:

<img src="../../images/valid_compare.png" alt="Image 5" style="max-width: 70%; display: inline-block;">

And a more granular way of analyzing this plot is by calculating the residuals, throwing those on a histogram, and doing a guassian fit:

<img src="../../images/valid_residuals.png" alt="Image 5" style="max-width: 70%; display: inline-block;">

The good news about this plot is it means in the majority of cases, the predicted z value of annihilation is within 15 mm of the real z position of annihilation. The bad news is that these results still lag behind the traditional computational method and so more work was needed for the ML method to beat and not just compliment, or backup, the traditional method. 

That has been thoroughly achieved now though, with the ML method having significantly better resolution than the conventional method:
<img src="../../images/alpha_res.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

And finally, we deeply care about z-dependant bias as this is a scientific experiment where all contributions of systematic bias need to be as low as possible. This bias is something the ML method struggled with for a long time but that recently has been solved:
<img src="../../images/alpha_bias.png" alt="Image 5" style="max-width: 100%; display: inline-block;">


## Conclusion 

These results are very promising! Good enough that this model will likely be used in actual analysis some day which is very exciting to me. 


## Resources

- Code is currently available through the internal TRIUMF GitLab and will hopefully be made publicly available too:

<img src="../../images/gitlab.png" alt="Image 5" style="max-width: 100%; display: inline-block;">


- Poster (**with more up-to-date results**) available [here](https://indico.triumf.ca/event/509/contributions/5908/)

<img src="../../images/sci_week_poster.png" alt="Image 8" style="max-width: 80%; display: inline-block;">
