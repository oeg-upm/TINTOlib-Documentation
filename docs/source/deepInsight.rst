DeepInsight
===========

The DeepInsight method transforms non-image tabular data into synthetic images by spatially arranging features based on their similarity. The process begins by applying dimensionality reduction techniques (such as t-SNE, PCA, or Kernel PCA) to project the feature space into a 2-dimensional plane. A convex hull algorithm is then employed to identify the smallest rectangle encompassing the feature points, which is subsequently rotated to align with the image axes. Finally, the feature values are mapped to the corresponding pixel locations within this grid. This structured arrangement ensures that correlated features are placed in proximity, enabling Convolutional Neural Networks (CNNs) to exploit local spatial dependencies effectively.

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/DEEPINSIGHT_CENTROIDS_000807.png
   :width: 200px
   :align: center
   :alt: Image created by the DeepInsight method, visualizing data transformed using dimensionality reduction and convex hull framing.

Import DeepInsight
------------------
To import DeepInsight model use:

>>> from TINTOlib.deepInsight import DeepInsight
>>> model = DeepInsight(image_dim=30)

Hyperparameters & Configuration
-------------------------------

When creating the :py:class:`DeepInsight` class, some parameters can be modified. The parameters are:

.. list-table::
   :widths: 20 40 20 20
   :header-rows: 1

   * - Parameters
     - Description
     - Default value
     - Valid values
   * - :py:data:`image_dim`
     - Order size for a square matrix image.
     - **Required**
     - integer
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
   * - :py:data:`algorithm_rd`
     - Dimensionality reduction algorithm to determine feature coordinates.
     - 'PCA'
     - ['PCA', 't-SNE', 'kPCA']
   * - :py:data:`assignment_method`
     - Technique to map features to pixels.
     - 'bin'
     - str (e.g., 'bin')
   * - :py:data:`relocate`
     - Relocate features so that each pixel can represent a single feature (only if algorithm_rd is 'PCA').
     - False
     - [True, False]
   * - :py:data:`algorithm_opt`
     - Optimization algorithm applied in the pixel assignment stage.
     - 'linear_sum'
     - str (e.g., 'linear_sum')
   * - :py:data:`group_method`
     - Technique to calculate pixel values sharing multiple features.
     - 'avg'
     - 'avg'
   * - :py:data:`zoom`
     - Multiplication factor determining the size of the saved image relative to the original size.
     - 1
     - integer > 0
   * - :py:data:`format`
     - Output format using images with matplotlib with [0,255] range for pixel or using npy format.
     - 'png'
     - ['png', 'npy']
   * - :py:data:`cmap`
     - Color map to use with matplotlib.
     - 'gray'
     - 'viridis', 'plasma', 'inferno', 'magma', 'cividis', 'Greys', etc.
   * - :py:data:`random_seed`
     - Seed for reproducibility.
     - 23
     - integer

Code example:

>>> model = DeepInsight(image_dim=50, algorithm_rd='t-SNE', cmap='viridis', random_seed=42)

All the parameters that aren't specifically set will have their default values.

Functions
---------
DeepInsight has the following functions:

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
     - Load DeepInsight configuration previously saved with :py:data:`saveHyperparameters(filename)`

       - filename: .pkl file path
     -
   * - :py:data:`fit(data)`
     - Trains the model on the tabular data. This step performs dimensionality reduction to map features to the 2D grid.

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
**Paper**: https://doi.org/10.1038/s41598-019-47765-6

**Code Repository**: https://github.com/alok-ai-lab/pyDeepInsight