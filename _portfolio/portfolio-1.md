---
title: "Self-Supervised Learning for Astronomy"
excerpt: "Specifically exploring reconstruction-based methods like masked image modelling<br/><img src='../images/tsne.png' style="max-width: 100%; display: inline-block;">"
collection: portfolio
tags:
- python
- pytorch
- multi-GPU
---

## TL;DR

Masking images and making a model reconstruct the missing pixels is a meaningful task to get a deep learning model to learn some fundamental patterns in astronomy data. 

## Abstract

The Ultraviolet Near Infrared Optical Northern Survey (UNIONS) uses observations from three telescopes in Hawaii to investigate some of the most fundamental questions in astrophysics, such as determining the properties of dark matter and dark energy, as well as the growth of structure in the Universe. However, it is difficult to effectively search through and categorize UNIONS data to address these questions due to the volume of data produced. This project aims to exploit advances in a sub-field of Machine Learning (ML) called Self-Supervised Learning (SSL), to train a model to produce astrophysically meaningful representations of astronomy observations. This is done solely by training it on images of the sky, without the need for explicit labels indicating what source is being observed. When paired with a small number of labelled examples, these representations are useful in downstream tasks such as similarity searches for rare astronomical objects, or as inputs to a linear regression layer to predict redshifts. For this report, a SSL masked image modeling method was implemented and evaluated on a specific use case of dwarf galaxy identification. By simply inputting the learned representations of 200 dwarf galaxy examples and 200 non-dwarf galaxies to a linear regression layer, the model achieves upwards of 90\% accuracy in identifying known dwarf galaxies. Further, a similarity search is performed using the representations of just a handful of dwarf galaxies and 23 of the top 25 most similar sources are found to be dwarf galaxies. These results prove this method is a promising avenue to explore for not only the discovery of more dwarf galaxies but various other tasks of interest to astronomers. 

## Method

<img src="../images/project_goal3.png" alt="Image 5" style="max-width: 100%; display: inline-block;">