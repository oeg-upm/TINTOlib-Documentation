TINTO
=====

The TINTO method transforms tabular data into images by first reducing dimensions using PCA or t-SNE, then mapping features to a 2D grid based on their center of gravity. It finalizes pixel positions by rounding coordinates and applies a blurring effect to blend feature values into neighboring pixels.

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/BarGraph_zoom2_005854_zoom.png
   :width: 300px
   :align: center

Import TINTO
----------------
To import TINTO model use:

>>> from TINTOlib.tinto import TINTO
>>> model = TINTO()

Hyperparameters & Configuration
---------------

When creating the :py:class:`tinto` class, some parameters can be modified. The parameters are:


.. list-table::
   :widths: 20 40 20 20
   :header-rows: 1

   * - Parameters
     - Description
     - Default value
     - Valid values
   * - :py:data:`problem`
     - The type of problem, defining how the images are grouped.
     - 'supervised'
     - ['supervised', 'unsupervised', 'regression']
   * - :py:data:`normalize`
     - If True, normalizes input data using MinMaxScaler.
     - True
     - [True, False]
   * - :py:data:`verbose`
     - Show execution details in the terminal.
     - False
     - [True, False]
   * - :py:data:`pixels`
     - The number of pixels used to create the image (one side); total pixels = pixels * pixels.
     - 20
     - integer
   * - :py:data:`algorithm`
     - Select the dimensionality reduction algorithm.
     - 'PCA'
     - ['PCA', 't-SNE']
   * - :py:data:`blur`
     - Activate or deactivate the blurring option.
     - False
     - [True, False]
   * - :py:data:`submatrix`
     - Specifies whether to use a submatrix for blurring.
     - True
     - [True, False]
   * - :py:data:`amplification`
     - Only used when `blur=True`. Specifies the blurring amplification.
     - :py:data:`np.pi`
     - float
   * - :py:data:`distance`
     - Only used when `blur=True`. Specifies the blurring distance (number of pixels).
     - 2
     - integer
   * - :py:data:`steps`
     - Only used when `blur=True`. Specifies the number of blurring steps.
     - 4
     - integer
   * - :py:data:`option`
     - Only used when `blur=True`. Technique for handling overlapping pixels.
     - 'mean'
     - ['mean', 'maximum']
   * - :py:data:`times`
     - Only used when `algorithm='t-SNE'`. Specifies the replication times in t-SNE.
     - 4
     - integer
   * - :py:data:`zoom`
     - Multiplication factor determining the size of the saved image relative to the original size. Values greater than 1 increase the image size proportionally.
     - 1
     - integer
   * - :py:data:`random_seed`
     - Seed for reproducibility.
     - 1
     - integer


Code example:

>>> model = TINTO(algorithm="t-SNE",pixels=30,blur=True,option="maximum")

All the parameters that aren't expecifically setted will have their default values.

Functions
---------
TINTO has the following functions:

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
**Paper**: https://doi.org/10.1016/j.inffus.2022.10.011

**Code Repository**: https://github.com/oeg-upm/TINTO

