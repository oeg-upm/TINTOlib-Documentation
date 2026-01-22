Fotomics
========

The Fotomics method transforms tabular data into synthetic images using the Fourier Transform. It computes the Fourier Transform of the input set, averages the real and imaginary values across samples to determine feature coordinates, and maps them to a 2D grid. This implementation extends the original method by allowing different mapping techniques, outlier treatments, and pixel value calculations.

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/FOTOMICS_OT19Z_GPAVG_000086.png
   :width: 200px
   :align: center
   :alt: Image created by the Fotomics method, visualizing data transformed using the Fourier Transform.

Import Fotomics
---------------
To import Fotomics model use:

>>> from TINTOlib.fotomics import Fotomics
>>> model = Fotomics(image_dim=30)

Hyperparameters & Configuration
-------------------------------

When creating the :py:class:`Fotomics` class, some parameters can be modified. The parameters are:

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
     - LogScaler()
     - Scikit Learn transformers or custom implementation inheriting CustomTransformer.
   * - :py:data:`verbose`
     - Show execution details in the terminal.
     - False
     - [True, False]
   * - :py:data:`outliers`
     - Treat outliers after Fourier transform.
     - True
     - [True, False]
   * - :py:data:`min_percentile`
     - Minimum percentile for outlier detection.
     - 10
     - integer
   * - :py:data:`max_percentile`
     - Maximum percentile for outlier detection.
     - 90
     - integer
   * - :py:data:`outliers_treatment`
     - Technique to treat outliers.
     - 'zero'
     - ['zero', 'max_min', 'avg']
   * - :py:data:`assignment_method`
     - Technique to map features to pixels.
     - 'bin_digitize'
     - str (e.g., 'bin_digitize')
   * - :py:data:`relocate`
     - Relocate features so that each pixel can represent a single feature.
     - False
     - [True, False]
   * - :py:data:`algorithm_opt`
     - Optimization algorithm applied in the pixel assignment stage.
     - 'linear_sum'
     - str (e.g., 'linear_sum')
   * - :py:data:`group_method`
     - Technique to calculate pixel values sharing multiple features.
     - 'avg'
     - str (e.g., 'avg')
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
     - 1
     - integer

Code example:

>>> model = Fotomics(image_dim=30, outliers=False, zoom=2)

All the parameters that aren't specifically set will have their default values.

Functions
---------
Fotomics has the following functions:

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
     - Load Fotomics configuration previously saved with :py:data:`saveHyperparameters(filename)`

       - filename: .pkl file path
     -
   * - :py:data:`fit(data)`
     - Trains the model on the tabular data. This step computes the Fourier Transform and determines feature coordinates.

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
**Paper**: https://doi.org/10.1007/s10462-022-10357-4

**Code Repository**: https://github.com/VafaeeLab/Fotomics-Imagification