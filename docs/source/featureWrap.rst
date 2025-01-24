FeatureWrap
=====

Import FeatureWrap
----------------
To import FeatureWrap model use:

>>> from TINTOlib.featureWrap import FeatureWrap
>>> model = FeatureWrap()

Hyperparameters & Configuration
---------------

When creating the :py:class:`FeatureWrap` class, some parameters can be modified. The parameters are:


.. list-table::
   :widths: 20 40 20 20
   :header-rows: 1

   * - Parameters
     - Description
     - Default value
     - Valid values
   * - :py:data:`problem`
     - Defines how the images are grouped based on the type of problem.
     - 'supervised'
     - ['supervised', 'unsupervised', 'regression']
   * - :py:data:`normalize`
     - Normalizes input data using MinMaxScaler if set to True.
     - True
     - [True, False]
   * - :py:data:`verbose`
     - Displays execution details in the terminal if set to True.
     - False
     - [True, False]
   * - :py:data:`size`
     - Specifies the width and height of the final image in pixels (rows x columns).
     - (8, 8)
     - tuple of two positive integers
   * - :py:data:`bins`
     - Determines the number of bins or intervals used for grouping numeric data.
     - 10
     - integer > 1
   * - :py:data:`zoom`
     - Sets the multiplication factor for resizing the image relative to its original size.
     - 1
     - integer > 0




Code example:

>>> model = FeatureWrap(size=[10,10], bins=20)

All the parameters that aren't expecifically setted will have their default values.

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
     - Allows to save the defined parameters (scale, fea_dost_method, image_dist_method, etc.)
     - .pkl file with the configuration
   * - :py:data:`loadHyperparameters(filename)`
     - Load TINTO configuration previously saved with :py:data:`saveHyperparameters(filename)`

        - filename: .pkl file path
     -
   * - :py:data:`fit(data)`
     - Trains the model on the tabular data and prepares it for image generation.

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
------
**Paper**: https://doi.org/10.1007/978-3-319-70139-4_87

**Code Repository**: 
