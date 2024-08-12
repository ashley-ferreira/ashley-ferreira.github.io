---
title: "Automated Analysis of Strong Gravitational Lenses"
excerpt: "<img src='../images/strong_lens_sim.png' style='max-width: 60%; display: inline-block;'>"
collection: portfolio
tags:
- python
- pytorch
- computer vision
---

## Overview 

The Astromatic summer program is run by the Ciela Institute at Université de Montréal and I participated in its inaugural year in 2022. This program selected 15 outstanding undergraduate students from 8 different countries converged in Montréal for three days of expert lectures on foundational topics and research, programming workshops and career activities.\\(^1\\) 

The week culminated in an astro-ML hackathon, where I worked as part of a team of 3 to train a ResNet deep learning model to estimate parameters of strong gravitational lensing from simulated images:

<img src="../../images/strong_lens_sim.png" alt="Image 5" style="max-width: 70%; display: inline-block;">

Strong gravitational lensing is a rare and extremely interesting astrophysical event where space-time itself it warped by the emmense graviaty of celestial objects. Observing and analyzing examples of this give us insight into areas of high interest such as dark matter.

For the most part, most variables representing various characteristics of the strong lenses were reasonably reconstructed by the model:

<img src="../../images/lens_results_1.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

While there were still significant errors, certain variables were completely failed at being reconstructed by the model. However, on closer inspection these characteristics had much to due with the object being lensed and so once the foreground object was removed, and the variables were also parameterized differently, more reasonable, yet still lacking, predictions were possible:

<img src="../../images/lens_results_2.png" alt="Image 5" style="max-width: 70%; display: inline-block;">

## Built With
[![Python][python]][python-url]
[![Notebook][notebook]][notebook-url] 
[![PyTorch][pytorch]][pytorch-url]
[![WandB][wandb]][wandb-url] 
[![github][github]][github-url]

[github]: https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white
[github-url]: https://github.com/

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


## Resources

Sadly code is not publicly available as it directly builds on private lens modelling code from a graduate student.


\\(^1\\) [www.astro.umontreal.ca/astromatic/2022/](https://www.astro.umontreal.ca/astromatic/2022/)