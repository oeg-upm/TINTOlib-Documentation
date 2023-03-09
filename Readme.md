## Data2Image

[![License](https://img.shields.io/badge/license-Apache%202.0-blue)](https://github.com/manwestc/TINTO/blob/main/LICENSE)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7463973.svg)](https://doi.org/10.5281/zenodo.7463973)
[![Python Version](https://img.shields.io/badge/Python-3.7%20%7C%203.8%20%7C%203.9%20%7C%203.10%20%7C%203.11-blue)](https://pypi.python.org/pypi/)
[![Documentation Status](https://readthedocs.org/projects/morph-kgc/badge/?version=latest)]()
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/)

**Data2Image** is a state-of-the-art library that wraps the most important techniques for the construction of **Synthetic Images** from [Sorted Data](https://www.jstatsoft.org/article/view/v059i10) (also known as **Tabular Data**). 

## Features
- Input data formats:
    - **Pandas Dataframe** : DOING
    - **Files with the following format** 
        - **Tabular files**: The input data must be in **[CSV](https://en.wikipedia.org/wiki/Comma-separated_values)**, taking into account the **[Tidy Data](https://www.jstatsoft.org/article/view/v059i10)** format.
        - **Tidy Data**: The **target** (variable to be predicted) should be set as the last column of the dataset. Therefore, the first columns will be the features.
        - All data must be in numerical form.
        
- Runs on **Linux**, **Windows** and **macOS** systems.
- Compatible with **[Python](https://www.python.org/)** 3.7 or higher.

## Methods

- **[TINTO](https://github.com/oeg-upm/TINTO)**.

## Documentation

[Read the documentation](https://documentationtinto.readthedocs.io/en/latest/).
## Getting Started

**[TINTO](https://github.com/oeg-upm/TINTO)** is easy to use in terminal:

Fist, it is important to install all previus libraries
```
    pip install -r requirements.txt
```


To run the engine via **command line** and see all the **arguments** you just need to execute the following:
```
    python tinto.py -h
```

![Help](https://github.com/manwestc/TINTO/blob/main/imgs/tinto_help.png)

The default parameter are the following:
- **Dimensional Reduction Algorithm (-alg)**: Select the dimensionality reduction algorithm to be used for image creation. The [PCA](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html#sklearn.decomposition.PCA)** or [*t*-SNE](https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html) algorithms can be chosen. By default, use the [PCA](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html#sklearn.decomposition.PCA)** algorithm.
- **Image size (-px)**: 20x20 pixels
- **Blurring (-B)**: for default is False, i.e., it do not use Blurring technique and create de images with characteristic pixels
- **Amplification (-aB)**: Only if Blurring is True. It is the blurring amplification and for default is PI number, i.e., 3.141592653589793 aprox.
- **Blurring distance (-dB)**: Only if Blurring is True. It is Blurring distance and for default is 0.1 (10%).
- **Blurring steps (-sB)**: Only if Blurring is True. It is Blurring steps and for default is 4, i.e., expand 4 pixels the blurring.
- **Blurring option (-oB)**: Only if Blurring is True. It is the Blurring option and for default is _mean_, i.e., if two pixels are overlaping, calculate the average number of this two overlaping pixels.
- **Save Configuration (-sC)**: Save the configurarion in a pikle object. It is False for default.
- **Load Configuration (-lC)**: Load the configurarion in a pikle object. It is False for default.
- **Seed (-sd)**: Set a seed for the random numbers. It is 20 for default.
- **_t_SNE times replication (-tt)**: It is only used when _t_-SNE is used. It is _t_-SNE times replication and for defaultd is 4.
- **Verbose (-v)**. Show in terminal the execution. For default is False.

## License

Data2Image is available under the **[Apache License 2.0](https://github.com/manwestc/TINTO/blob/main/LICENSE)**.

## Authors

- **[Manuel Castillo-Cara](https://github.com/manwestc) - [jcastillo@fi.upm.es](mailto:jcastillo@fi.upm.es)**
- **[Raúl García-Castro](https://github.com/rgcmme)**

*[Ontology Engineering Group](https://oeg.fi.upm.es)*, *[Universidad Politécnica de Madrid](https://www.upm.es/internacional)*.




