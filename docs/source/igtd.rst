IGTD
=====


The Image Generator for Tabular Data (IGTD) method transforms tabular data into images by arranging features according to their similarity. Initially, it creates a similarity matrix using techniques such as Pearson or Spearman correlation to evaluate the relationships between features. Subsequently, it computes a matrix that represents the spatial distances between pixel positions in the image. Finally, IGTD rearranges the features to ensure that the layout of the similarity matrix closely matches the spatial arrangement in the image, refining the placement iteratively.

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/IGTD_40x40_fEuclidean_iEuclidean_abs_000100_zoom.png
   :width: 200px
   :align: center
   :alt: Synthetic image produced by the IGTD method.

---

Import IGTD
----------------
To import IGTD model use:

>>> from TINTOlib.igtd import IGTD
>>> model = IGTD()

Hyperparameters & Configuration
---------------

When creating the :py:class:`IGTD` class, some parameters can be modified. The parameters are:


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
   * - :py:data:`scale`
     - The number of pixel rows and columns in the image. The product (rows x columns) must be greater than or equal to the number of features.
     - [6, 6]
     - list of two positive integers
   * - :py:data:`fea_dist_method`
     - Method to calculate pairwise distances between features.
     - 'Pearson'
     - ['Pearson', 'Spearman', 'set', 'Euclidean']
   * - :py:data:`image_dist_method`
     - Method to calculate distances between pixels in the image.
     - 'Euclidean'
     - ['Euclidean', 'Manhattan']
   * - :py:data:`error`
     - Function to evaluate differences between feature and pixel distance rankings.
     - 'squared'
     - ['squared', 'abs']
   * - :py:data:`max_step`
     - Maximum number of iterations for the algorithm if it does not converge.
     - 1000
     - integer
   * - :py:data:`val_step`
     - Number of steps to check gain on the objective function for convergence.
     - 50
     - integer
   * - :py:data:`switch_t`
     - Threshold for error change rate to determine if switching features should occur.
     - 0
     - integer
   * - :py:data:`min_gain`
     - Minimum improvement in the objective function to continue optimization.
     - 0.00001
     - float
   * - :py:data:`zoom`
     - Multiplication factor determining the size of the saved image relative to the original size.
     - 1
     - integer > 0
   * - :py:data:`random_seed`
     - Seed for reproducibility.
     - 1
     - integer




Code example:

>>> model = IGTD(scale=[3,3],error="abs",val_step=60)

All the parameters that aren't expecifically setted will have their default values.

Functions
---------
IGTD has the following functions:

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
**Paper**: https://doi.org/10.1038/s41598-021-90923-y

**Code Repository**: https://github.com/zhuyitan/igtd
