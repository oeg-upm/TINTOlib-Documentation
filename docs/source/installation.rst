Introduction
=====
This documentation provides detailed instructions on how to install, configure, and use TINTOlib—a Python library designed to transform tabular data into synthetic images, enabling the application of advanced vision-based machine learning models on traditional data sets.

.. _installation:

Installation
------------

To use TINTOlib, first install it using `PyPi <https://pypi.org/project/TINTOlib>`_:

.. code-block:: console

   (.venv) $ pip install TINTOlib

For more details, visit: TINTOlib on PyPI <https://pypi.org/project/TINTOlib>

Additional Resources
####################

- `TINTOlib Crash Course <https://github.com/oeg-upm/TINTOlib-Crash_Course/tree/main>`_  
  Hands-on notebooks and slides showing how to use CNNs, ViTs, and Hybrid Neural Networks (HyNNs) with TINTOlib.

- `TINTOlib GitHub Repository <https://github.com/oeg-upm/TINTOlib>`_  
  Main codebase with transformation methods, examples, and full documentation.

Importing Methods
----------------
TINTOlib offers a variety of state-of-the-art methods for constructing synthetic images from tabular data. To use these methods, import the required models as shown below:

>>> from TINTOlib.tinto import TINTO
>>> from TINTOlib.igtd import IGTD

All the methods requires the same input format and the responses outputs will have the same format.

Available Methods
--------------
.. list-table::
   :widths: 25 25 50
   :header-rows: 1

   * - Models
     - Class
     - Hyperparameters
   * - `TINTO <https://github.com/oeg-upm/TINTO>`_
     - ``TINTO()``
     - `problem`, `normalize`, `verbose`, `pixels`, `algorithm`, `blur`, `submatrix`, `amplification`, `distance`, `steps`, `option`, `times`, `train_m`, `zoom`, `random_seed`
   * - `IGTD <https://github.com/zhuyitan/igtd>`_
     - ``IGTD()``
     - `problem`, `normalize`, `verbose`, `scale`, `fea_dist_method`, `image_dist_method`, `error`, `max_step`, `val_step`, `switch_t`, `min_gain`, `zoom`, `random_seed`
   * - `REFINED <https://github.com/omidbazgirTTU/REFINED>`_
     - ``REFINED()``
     - `problem`, `normalize`, `verbose`, `hcIterations`, `n_processors`, `zoom`, `random_seed`
   * - `BarGraph <https://github.com/anuraganands/Non-image-data-classification-with-CNN/>`_
     - ``BarGraph()``
     - `problem`, `normalize`, `verbose`, `pixel_width`, `gap`, `zoom`
   * - `DistanceMatrix <https://github.com/anuraganands/Non-image-data-classification-with-CNN/>`_
     - ``DistanceMatrix()``
     - `problem`, `normalize`, `verbose`, `zoom`
   * - `Combination <https://github.com/anuraganands/Non-image-data-classification-with-CNN/>`_
     - ``Combination()``
     - `problem`, `normalize`, `verbose`, `zoom`
   * - `SuperTML <https://github.com/GilesStrong/SuperTML_HiggsML_Test>`_
     - ``SuperTML()``
     - `problem`, `normalize`, `verbose`, `pixels`, `feature_importance`, `font_size`, `random_seed`
   * - `FeatureWrap <https://link.springer.com/chapter/10.1007/978-3-319-70139-4_87>`_
     - ``FeatureWrap()``
     - `problem`, `normalize`, `verbose`, `size`, `bins`, `zoom`
   * - `BIE <https://ieeexplore.ieee.org/document/10278393>`_
     - ``BIE()``
     - `problem`, `normalize`, `verbose`, `precision`, `zoom`

Input Format
------------
TINTOlib supports two primary data input formats:

Pandas DataFrame
################
- Use a Pandas DataFrame with the target variable in the **last column** and features in other columns, all in numerical format.
- Follow the `Tidy Data <https://www.jstatsoft.org/article/view/v059i10>`_ principles.

CSV Files
#########
- Format your CSV with commas as separators and the target variable in the **last column**.
- Ensure the first row contains feature names and all data is numerical.

**Example Usage:**

.. code-block:: bash

   model = TINTO()
   model.fit_transform('path_to_csv_file', 'result_folder_path')

Generating Synthetic Images
---------------------------
To generate synthetic images, TINTOlib provides `fit`, `transform`, and `fit_transform` methods:

**Fitting the Model:**
The `fit` method trains the model on the tabular data:

.. code-block:: python

   model.fit(data)

**Generating Synthetic Images:**
After fitting, use `transform` to generate and save images:

.. code-block:: python

   model.transform(data, folder)

**Combining Fit and Transform:**
The `fit_transform` method combines training and image generation:

.. code-block:: python

   model.fit_transform(data, folder)

**Parameters for Methods:**
- **data**: A path to a CSV file or a Pandas DataFrame containing the features and targets.
- **folder**: Path where the synthetic images will be saved.

Output Format
-------------
The output of the :py:func:`model.transform(data,folder)` and :py:func:`model.fit_transform(data,folder)` method are synthetic images grouped in folders depending on their class value.

For example: 

If the dataset is composed of 3 different classes, the method will create 3 folders and each folder will contain one synthetic image for each instance with that class.

---

Example Generated Synthetic Images using TINTOlib
--------------

This section provides visual examples of synthetic images generated by different methods in TINTOlib.

**TINTO Method**

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/TINTO_blur_maximum_000100_zoom.png
   :width: 200px
   :align: center
   :alt: Synthetic image generated using the TINTO method with maximum blurring.

**IGTD Method**

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/IGTD_40x40_fEuclidean_iEuclidean_abs_000100_zoom.png
   :width: 200px
   :align: center
   :alt: Synthetic image produced by the IGTD method, showcasing feature organization based on similarity.

**REFINED Method**

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/REFINED_000100_zoom.png
   :width: 200px
   :align: center
   :alt: Example of a synthetic image from the REFINED method, highlighting optimized feature placement.

**BarGraph Method**

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/BarGraph_zoom2_005854_zoom.png
   :width: 200px
   :align: center
   :alt: Image created by the BarGraph method, visualizing data as a series of bars.

**DistanceMatrix Method**

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/DistanceMatrix_zoom2_005854_zoom.png
   :width: 200px
   :align: center
   :alt: DistanceMatrix method where distances represent feature relationships.

**Combination Method**

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/Combination_zoom2_005854_zoom.png
   :width: 200px
   :align: center
   :alt: Combination method image, integrating features of the BarGraph and DistanceMatrix methods.

**SuperTML Method**

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/SuperTML-EF_005854_zoom.png
   :width: 200px
   :align: center
   :alt: Synthetic image generated using the SuperTML-EF method, featuring uniform font size for all features.

**FeatureWrap Method**

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/FeatureWrap_264844_zoom.png
   :width: 200px
   :align: center
   :alt: FeatureWrap method image, encoding features as binary vectors transformed into pixel values.

**BIE Method**

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/BIE_000000_zoom.png
   :width: 200px
   :align: center
   :alt: BIE method image, depicting binary encoded floating-point representations as black and white pixels.


