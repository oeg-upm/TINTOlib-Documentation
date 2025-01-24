# TINTOlib: Python Library to convert Tabular Data into Synthetic Images

[![License](https://img.shields.io/badge/license-Apache%202.0-blue)](https://github.com/oeg-upm/TINTOlib-Documentation/blob/main/LICENSE)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue)](https://github.com/oeg-upm/TINTOlib-Documentation/blob/main/LICENSE)
[![Python Version](https://img.shields.io/badge/Python-3.7%20%7C%203.8%20%7C%203.9%20%7C%203.10%20%7C%203.11-blue)](https://pypi.python.org/pypi/)
[![Documentation Status](https://readthedocs.org/projects/morph-kgc/badge/?version=latest)](https://tintolib.readthedocs.io/en/latest/)
[![Open In Colab-CNN](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/oeg-upm/TINTOlib-Crash_Course/blob/main/Notebooks/Challenge/Regression_CNN.ipynb)
[![Open In Colab-CNN+MLP](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/oeg-upm/TINTOlib-Crash_Course/blob/main/Notebooks/Challenge/Regression_CNN%2BMLP.ipynb)
[![Open In Colab-ViT](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/oeg-upm/TINTOlib-Crash_Course/blob/main/Notebooks/Challenge/Regression_ViT.ipynb)
[![Open In Colab-ViT+MLP](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/oeg-upm/TINTOlib-Crash_Course/blob/main/Notebooks/Challenge/Regression_ViT%2BMLP.ipynb)


<div>
<p align = "center">
<img src="imgs/logo.svg" alt="TINTO Logo" width="150">
</p>
</div>

**[TINTOlib](https://tintolib.readthedocs.io/en/latest/)** is a state-of-the-art Python library that transforms **tidy data** (also known as tabular data) into **synthetic images**, enabling the application of advanced deep learning techniques, including **Vision Transformers (ViTs)** and **Convolutional Neural Networks (CNNs)**, to traditionally structured data. This transformation bridges the gap between tabular data and powerful vision-based machine learning models, unlocking new possibilities for tackling regression, classification, and other complex tasks.

**Citing TINTO**: If you used TINTO in your work, please cite the **[SoftwareX](https://doi.org/10.1016/j.softx.2023.101391)**:

```bib
@article{softwarex_TINTO,
    title = {TINTO: Converting Tidy Data into Image for Classification with 2-Dimensional Convolutional Neural Networks},
    journal = {SoftwareX},
    author = {Manuel Castillo-Cara and Reewos Talla-Chumpitaz and Raúl García-Castro and Luis Orozco-Barbosa},
    volume={22},
    pages={101391},
    year = {2023},
    issn = {2352-7110},
    doi = {https://doi.org/10.1016/j.softx.2023.101391}
}
```

And use-case developed in **[INFFUS Paper](https://doi.org/10.1016/j.inffus.2022.10.011)** 

```bib
@article{inffus_TINTO,
    title = {A novel deep learning approach using blurring image techniques for Bluetooth-based indoor localisation},
    journal = {Information Fusion},
    author = {Reewos Talla-Chumpitaz and Manuel Castillo-Cara and Luis Orozco-Barbosa and Raúl García-Castro},
    volume = {91},
    pages = {173-186},
    year = {2023},
    issn = {1566-2535},
    doi = {https://doi.org/10.1016/j.inffus.2022.10.011}
}
```

## Features
- Input data formats (2 options):
    - **Pandas Dataframe** 
    - **Files with the following format** 
        - **Tabular files**: The input data must be in **[CSV](https://en.wikipedia.org/wiki/Comma-separated_values)**, taking into account the **[Tidy Data](https://www.jstatsoft.org/article/view/v059i10)** format.
        - **Tidy Data**: The **target** (variable to be predicted) should be set as the last column of the dataset. Therefore, the first columns will be the features.
        - All data must be in numerical form.
        
- Runs on **Linux**, **Windows** and **macOS** systems.
- Compatible with **[Python](https://www.python.org/)** 3.7 or higher.

---

## Models

| Models | Class | Hyperparameters |
|:----------------------------------------------------------------:|:------------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| [TINTO](https://github.com/oeg-upm/TINTO) | `TINTO()` | `problem` `normalize` `verbose` `pixels` `algorithm` `blur` `submatrix` `amplification` `distance` `steps` `option` `times` `train_m` `zoom` `random_seed` |
| [IGTD](https://github.com/zhuyitan/igtd) | `IGTD()` | `problem` `normalize` `verbose` `scale` `fea_dist_method` `image_dist_method` `error` `max_step` `val_step` `switch_t` `min_gain` `zoom` `random_seed` |
| [REFINED](https://github.com/omidbazgirTTU/REFINED) | `REFINED()` | `problem` `normalize` `verbose` `hcIterations` `n_processors` `zoom` `random_seed` |
| [BarGraph](https://github.com/anuraganands/Non-image-data-classification-with-CNN/) | `BarGraph()` | `problem` `normalize` `verbose` `pixel_width` `gap` `zoom` |
| [DistanceMatrix](https://github.com/anuraganands/Non-image-data-classification-with-CNN/) | `DistanceMatrix()` | `problem` `normalize` `verbose` `zoom` |
| [Combination](https://github.com/anuraganands/Non-image-data-classification-with-CNN/) | `Combination()` | `problem` `normalize` `verbose` `zoom` |
| [SuperTML](https://github.com/GilesStrong/SuperTML_HiggsML_Test) | `SuperTML()` | `problem` `normalize` `verbose` `pixels` `feature_importance` `font_size` `random_seed` |
| [FeatureWrap](https://link.springer.com/chapter/10.1007/978-3-319-70139-4_87) | `FeatureWrap()` | `problem` `normalize` `verbose` `size` `bins` `zoom` |
| [BIE](https://ieeexplore.ieee.org/document/10278393) | `BIE()` | `problem` `normalize` `verbose` `precision` `zoom` |

---

## TINTOlib Crash Course:
[TINTOlib Crash Course](https://github.com/oeg-upm/TINTOlib-Crash_Course) repository provides a comprehensive crash course on using [TINTOlib](https://tintolib.readthedocs.io/en/latest/), a Python library designed to transform tabular data into synthetic images for machine learning tasks. It includes slides and Jupyter notebooks that demonstrate how to apply state-of-the-art vision models like Vision Transformers (ViTs) and Convolutional Neural Networks (CNNs) to problems such as regression and classification, using [TINTOlib](https://tintolib.readthedocs.io/en/latest/) for data transformation.

The repository also features Hybrid Neural Networks (HyNNs), where one branch is an MLP designed to process tabular data, while another branch—either CNN or ViT—handles the synthetic images. This architecture leverages the strengths of both data formats for enhanced performance on complex machine learning tasks. Ideal for those looking to integrate image-based deep learning techniques into tabular data problems.

---

## Converting Tidy Data into synthetic image

For example, the following table shows a classic example of the [IRIS CSV dataset](https://archive.ics.uci.edu/ml/datasets/iris) as it should look like for the run:


| sepal length | sepal width | petal length | petal width | target |
|--------------|-------------|--------------|-------------|--------|
| 4.9          | 3.0         | 1.4          | 0.2         | 1      |
| 7.0          | 3.2         | 4.7          | 1.4         | 2      |
| 6.3          | 3.3         | 6.0          | 2.5         | 3      |


### Simple example with TINTO method
The following example shows how to create 20x20 images with characteristic pixels, i.e. without blurring. 
Also, as no other parameters are indicated, you will choose the following parameters which are set by default:
- **Image size**: 20x20 pixels
- **Blurring**: No blurring will be used.
- **Seed**: with the seed set to 20.

<div>
<p align = "center">
<kbd><img src="imgs/characteristic.png" alt="TINTO characteristic pixel" width="250"></kbd>
</p>
</div>

---

## More information
- [TINTOlib Crash Course](https://github.com/oeg-upm/TINTOlib-Crash_Course)
- For more detailed information, refer to the **[TINTOlib ReadTheDocs](https://tintolib.readthedocs.io/en/latest/)**.  
- GitHub repository: **[TINTOlib Documentation](https://github.com/oeg-upm/TINTOlib-Documentation)**.
- PyPI: **[PyPI](https://pypi.org/project/TINTOlib/)**.

## License

TINTOlib is available under the **[Apache License 2.0](https://github.com/oeg-upm/TINTOlib-Documentation/blob/main/LICENSE)**.

## Authors
- **[Manuel Castillo-Cara](https://github.com/manwestc) - [manuelcastillo@dia.uned.es](manuelcastillo@dia.uned.es)**
- **[Raúl García-Castro](https://github.com/rgcmme) - [r.garcia@upm.es](r.garcia@upm.es)**
- **[Jiayun Liu](https://github.com/DCY1117) - [jiayun.liu@upm.es](jiayun.liu@upm.es)**


## Contributors

<div>
<p align = "center">
<kbd><img src="assets/logo-oeg.png" alt="Ontology Engineering Group" width="150"></kbd> <kbd><img src="assets/logo-upm.png" alt="Universidad Politécnica de Madrid" width="150"></kbd> <kbd><img src="assets/logo-uned-.jpg" alt="Universidad Nacional de Educación a Distancia" width="231"></kbd> <kbd><img src="assets/logo-uclm.png" alt="Universidad de Castilla-La Mancha" width="115"></kbd> 
</p>
</div>


