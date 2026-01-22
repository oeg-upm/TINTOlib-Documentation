BIE
===

The Binary Image Encoding (BIE) method converts numeric values into black-and-white images by using the binary floating-point representation of numbers according to the IEEE 754 standard. Numeric values are encoded into binary, with each bit translated into image pixels: 0s as black (0) and 1s as white (255).

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/BIE_000000_zoom.png
   :width: 200px
   :align: center
   :alt: BIE method image, depicting binary encoded floating-point representations as black and white pixels.

Import BIE
----------
To import the BIE model, use:

>>> from TINTOlib.bie import BIE
>>> model = BIE()

Hyperparameters & Configuration
-------------------------------

When creating the :py:class:`BIE` class, some parameters can be modified. The parameters are:

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
   * - :py:data:`precision`
     - Specifies the precision of the binary encoding used in image generation.
     - 32
     - [32, 64]
   * - :py:data:`zoom`
     - Multiplication factor determining the size of the saved image relative to the original size.
     - 1
     - integer > 0

Code example:

>>> model = BIE(problem='regression', precision=64, zoom=2)

All the parameters that aren't specifically set will have their default values.

Functions
---------
BIE has the following functions:

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
     - Load BIE configuration previously saved with :py:data:`saveHyperparameters(filename)`

       - filename: .pkl file path
     -
   * - :py:data:`fit(data)`
     - Trains the model on the tabular data. For BIE, this step primarily handles setup as the transformation is stateless.

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
**Paper**: https://ieeexplore.ieee.org/document/10278393

**Code Repository**: https://jds-online.org/journal/JDS/article/1360/file/12976