Combination
===========

The Combination method merges the Equidistant Bar Graph and the Normalized Distance Matrix approaches into a single RGB image, enriching the visual representation of the data. Each channel in the RGB format highlights different aspects: one for individual variable magnitudes, and others for the relationships between variables.

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/Combination_zoom2_005854_zoom.png
   :width: 200px
   :align: center
   :alt: Combination method image, integrating features of the BarGraph and DistanceMatrix methods.

Import Combination
------------------
To import Combination model use:

>>> from TINTOlib.combination import Combination
>>> model = Combination()

Hyperparameters & Configuration
-------------------------------

When creating the :py:class:`Combination` class, some parameters can be modified. The parameters are:

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
   * - :py:data:`zoom`
     - Multiplication factor determining the size of the saved image relative to the original size.
     - 1
     - integer > 0

Code example:

>>> model = Combination(problem='regression', zoom=2)

All the parameters that aren't specifically set will have their default values.

Functions
---------
Combination has the following functions:

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
     - Load Combination configuration previously saved with :py:data:`saveHyperparameters(filename)`

       - filename: .pkl file path
     -
   * - :py:data:`fit(data)`
     - Trains the model on the tabular data. For Combination, this step primarily handles setup as the transformation is stateless.

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
**Paper**: https://doi.org/10.1038/s41598-022-26378-6

**Code Repository**: https://github.com/anuraganands/Non-image-data-classification-with-CNN