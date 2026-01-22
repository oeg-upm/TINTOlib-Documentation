TINTO
=====

The TINTO method transforms tabular data into synthetic images by projecting it into a two-dimensional space and applying visualization techniques. It projects features onto a 2D grid (using PCA or t-SNE), finalizes pixel positions, and optionally applies a blurring effect to blend feature values into neighboring pixels.

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/TINTO_blur_maximum_000100_zoom.png
   :width: 200px
   :align: center
   :alt: Synthetic image generated using the TINTO method with maximum blurring.

Import TINTO
----------------
To import TINTO model use:

>>> from TINTOlib.tinto import TINTO
>>> model = TINTO()

Hyperparameters & Configuration
-------------------------------

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
   * - :py:data:`pixels`
     - The number of pixels used to create the image (one side). Total pixels = pixels * pixels.
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
   * - :py:data:`format`
     - Output format using images with matplotlib with [0,255] range for pixel or using npy format.
     - 'png'
     - ['png', 'npy']
   * - :py:data:`cmap`
     - Color map to use with matplotlib. If images with unique channel is required this parameter must be None. Accepts standard Matplotlib colormaps.
     - 'binary'
     - 'viridis', 'plasma', 'inferno', 'magma', 'cividis', 'Greys', 'Purples', etc. or None
   * - :py:data:`random_seed`
     - Seed for reproducibility.
     - 1
     - integer

Code example:

>>> model = TINTO(algorithm="t-SNE", pixels=30, blur=True, option="maximum", cmap="viridis")

All the parameters that aren't specifically set will have their default values.

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