---
title: "Self-Supervised Learning for Astronomy Discoveries"
excerpt: "<img src='../images/tsne.png' style='max-width: 60%; display: inline-block;'>"
collection: portfolio
tags:
- python
- pytorch
- multi-GPU
- git
---

\* * * super preliminary work * * * 

## TL;DR

Masking images and making a Machine Learning (ML) model reconstruct the missing pixels is a meaningful task to get a model to learn cetain fundamental patterns in astronomy data. 

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


## Background

The Ultraviolet Near Infrared Optical Northern Survey (UNIONS) uses observations from three telescopes in Hawaii to investigate some of the most fundamental questions in astrophysics, such as determining the properties of dark matter and dark energy, as well as the growth of structure in the Universe. However, it is difficult to effectively search through and categorize UNIONS data to address these questions due to the volume of data produced. 

## Goal

This project aims to exploit advances in a sub-field of ML called Self-Supervised Learning (SSL), to train a model to produce astrophysically meaningful representations of astronomy observations. 

## Method

This work is done solely by training it on images of the sky, without the need for explicit labels indicating what source is being observed. When paired with a small number of labelled examples, these representations are useful in downstream tasks such as similarity searches for rare astronomical objects, or as inputs to a linear regression layer to predict redshifts. 

Most recently, a SSL masked image modeling method called SimMIM was implemented and evaluated on a specific use case of dwarf galaxy identification. 

<img src="../../images/project_goal3.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

## Results

The model is able to reconstruct the astronomy images pretty well:


<img src="../../images/simmim_reconstructions.png" alt="Image 6" style="max-width: 40%; display: inline-block;">

More importantly, useful repesentations are learned!

Similar observations are clustered together (which is super useful for similarity searches):


<img src="../../images/tsne.png" alt="Image 7" style="max-width: 100%; display: inline-block;">


Linear classifiers and regressors can be build on these embeddings to allow for learning from fewer labelled examples thaen is needed train a model of similar performance from scratch for a specific task. The example of a dwarf galaxy classifier is used and achieves 90\% accuracy at identifying known dwarf galaxy candidates with only 200 examples. 

Further, a similarity search is performed using the representations of just a handful of dwarf galaxies and 23 of the top 25 most similar sources are found to be dwarf galaxies:

<img src="../../images/sim_search_dwarf.png" alt="Image 8" style="max-width: 95%; display: inline-block;">

## Conclusion 

These results prove this method is a promising avenue to explore for not only the discovery of more dwarf galaxies but various other tasks of interest to astronomers. 

## Code

* Initial effort with MAE: [github.com/ashley-ferreira/AstroMASK](https://github.com/ashley-ferreira/AstroMASK)

* Most recent work with SimMIM: [github.com/teaghan/sky_embeddings](https://github.com/teaghan/sky_embeddings)

* Poster available [here](https://drive.google.com/file/d/1pCPDfRXtnYHVPDUMBkf0NiLSKzdy5JFE/view?usp=sharing)

<img src="../../images/ssl_poster.001.jpeg" alt="Image 8" style="max-width: 100%; display: inline-block;">
