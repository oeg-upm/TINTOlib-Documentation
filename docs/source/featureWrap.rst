FeatureWrap
===========

The FeatureWrap method transforms tabular data into synthetic images by encoding features as binary vectors. Categorical data are one-hot encoded, while numerical data are normalized, discretized, and then encoded. These binary vectors are concatenated, padded if necessary, and converted into pixel values ranging from 0 to 255 to create the final image.

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/FeatureWrap_264844_zoom.png
   :width: 200px
   :align: center
   :alt: FeatureWrap method image, encoding features as binary vectors transformed into pixel values.

Import FeatureWrap
------------------
To import FeatureWrap model use:

>>> from TINTOlib.featureWrap import FeatureWrap
>>> model = FeatureWrap()

Hyperparameters & Configuration
-------------------------------

When creating the :py:class:`FeatureWrap` class, some parameters can be modified. The parameters are:

.. list-table::
   :widths: 20 40 20 20
   :header-rows: 1

   * - Parameters
     - Description
     - Default value
     - Valid values
   * - :py:data:`problem`
     - The type of problem, defining how the images are grouped.
     - 'classification'
     - ['classification', 'unsupervised', 'regression']
   * - :py:data:`transformer`
     - Preprocessing transformations like scaling, normalization, etc.
     - MinMaxScaler()
     - Scikit Learn transformers or custom implementation inheriting CustomTransformer.
   * - :py:data:`verbose`
     - Show execution details in the terminal.
     - False
     - [True, False]
   * - :py:data:`size`
     - The width and height of the final image, in pixels (rows x columns).
     - (8, 8)
     - tuple of two positive integers
   * - :py:data:`bins`
     - The number of bins or intervals used for grouping numeric data.
     - 10
     - integer > 1
   * - :py:data:`zoom`
     - Multiplication factor determining the size of the saved image relative to the original size.
     - 1
     - integer > 0

Code example:

>>> model = FeatureWrap(size=(10, 10), bins=20, verbose=True)

All the parameters that aren't specifically set will have their default values.

Functions
---------
FeatureWrap has the following functions:

.. list-table::
   :widths: 20 60 20
   :header-rows: 1

   * - Function
     - Description
     - Output
   * - :py:data:`saveHyperparameters(filename)`
     - Allows to save the defined parameters.
     - .pkl file with the configuration
   * - :py:data:`loadHyperparameters(filename)`
     - Load FeatureWrap configuration previously saved with :py:data:`saveHyperparameters(filename)`

       - filename: .pkl file path
     -
   * - :py:data:`fit(data)`
     - Trains the model on the tabular data. For FeatureWrap, this step prepares the transformer but the primary logic is applied during transformation.

       - data: A path to a CSV file or a Pandas DataFrame containing the features and targets. The target column must be the last column.
     -
   * - :py:data:`transform(data, folder)`
     - Generates and saves synthetic images in a specified folder. Requires the model to be fitted first.

       - data: A path to a CSV file or a Pandas DataFrame containing the features and targets. The target column must be the last column.
       - folder: Path to the folder where the synthetic images will be saved.
     - Folders with synthetic images
   * - :py:data:`fit_transform(data, folder)`
     - Combines the training and image generation steps. Fits the model to the data and generates synthetic images in one step.

       - data: A path to a CSV file or a Pandas DataFrame containing the features and targets. The target column must be the last column.
       - folder: Path to the folder where the synthetic images will be saved.
     - Folders with synthetic images

- **The model must be fitted** before using the `transform` method. If the model isn't fitted, a `RuntimeError` will be raised.

Citation
--------
**Paper**: https://doi.org/10.1007/978-3-319-70139-4_87

**Code Repository**: https://github.com/oeg-upm/TINTO