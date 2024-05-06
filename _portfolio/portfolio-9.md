---
title: "Alouette-1 Ionogram Data Extraction"
excerpt: "<img src='../images/alouette.png' style='max-width: 60%; display: inline-block;'>"
collection: portfolio
tags:
- python
- computer vision
- GPU
- git
- keras
---

## Overview 

Alouette-1 is satellite that initiated Canada’s participation in space. At a time when satellites were designed and expected to last only a few months, but Alouette-1 transmitted data over 10 years to a growing international network of telemetry stations from 1962 – 72. The data manually extracted from tapes led to countless publications but then sat in an archive as these tapes slowly deteriorated. Now, the data has been scanned and digitized, which could be used with today’s computational methods to produce a more comprehensive model of Earth’s topside ionosphere or contribute to historical climate studies.

I helped contribute to the effort to the effort to digitize this data, primairily by providing estimates of the mapping quality from the tape scans to arrays of numbers and by performance optimization of the machine learning based optical character recognition (OCR) using multiprocessing and GPUs.


<img src="../../images/alouette.png" alt="Image 5" style="max-width: 90%; display: inline-block;">

## Built With
[![Python][python]][python-url]
[![Keras][keras]][keras-url]
[![Notebook][notebook]][notebook-url] 
[![github][github]][github-url]

[github]: https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white
[github-url]: https://github.com/

[python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[python-url]: https://www.python.org/

[notebook]: https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter
[notebook-url]: https://jupyter.org/

[keras]: https://img.shields.io/badge/Keras-%23D00000.svg?style=for-the-badge&logo=Keras&logoColor=white
[keras-url]: https://keras.io/


## Code

Code publically available on GitHub: [asc-csa/Alouette_extract](https://github.com/asc-csa/Alouette_extract)
