---
title: "WatChMaL: Water Cherenkov Machine Learning"
excerpt: "<img src='../images/watchmal.png' style='max-width: 60%; display: inline-block;'>"
collection: portfolio
tags:
- python
- computer vision
- multi-GPU
- git
- pytorch
---

## Overview 

T2K is a neutrino experiment designed to investigate how neutrinos change from one flavour to another as they travel. An intense beam of muon neutrinos is generated at the J-PARC nuclear physics site on the East coast of Japan and directed across the country to the Super-Kamiokande neutrino detector in the mountains of western Japan. The beam is measured once before it leaves the J-PARC site, using the near detector ND280, and again at Super-K: the change in the measured intensity and composition of the beam is used to provide information on the properties of neutrinos.\\(^1\\)

There are many people working on ways to reconstruct the initial neutrino event that causes Cherenkov light to be emitted and picked up by detectors the surrounding the large tank of water built to capture these interactions:

<img src="../../images/pmts.png" alt="Image 5" style="max-width: 50%; display: inline-block;">

I was able to train a model to reconstruct the x, y, and z positions of where the neutrino interaction happened within this tank:

<img src="../../images/watchmal.png" alt="Image 5" style="max-width: 100%; display: inline-block;">

There are still significant errors that need to be reduced before it can fully beat the traditional method though.

## Built With
[![Python][python]][python-url]
[![PyTorch][pytorch]][pytorch-url]
[![Notebook][notebook]][notebook-url] 
[![github][github]][github-url]

[github]: https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white
[github-url]: https://github.com/

[python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[python-url]: https://www.python.org/

[notebook]: https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter
[notebook-url]: https://jupyter.org/

[pytorch]: https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white
[pytorch-url]: https://pytorch.org/


## Resources

Code is publicly available through the following GitHub repositories:
- [felix-cormier/WatChMaL](https://github.com/felix-cormier/WatChMaL)
- [felix-cormier/t2k_ml](https://github.com/felix-cormier/t2k_ml)
- [felix-cormier/t2k_ml_training](https://github.com/felix-cormier/t2k_ml_training)

\\(^1\\) [www.triumf.ca/t2k-canada](https://www.triumf.ca/t2k-canada)