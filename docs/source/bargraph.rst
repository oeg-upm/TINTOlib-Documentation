BarGraph
=====

Import BarGraph
----------------
To import BarGraph model use:

>>> from TINTOlib.bargraph import BarGraph
>>> model = BarGraph()

Hyperparameters & Configuration
---------------

When creating the :py:class:`BarGraph` class, some parameters can be modified. The parameters are:


.. list-table::
   :widths: 20 40 20 20
   :header-rows: 1

   * - Parameters
     - Description
     - Default value
     - Valid values
   * - :py:data:`problem`
     - Specifies how the images are grouped based on the type of problem, influencing the method of data visualization.
     - 'supervised'
     - ['supervised', 'unsupervised', 'regression']
   * - :py:data:`normalize`
     - Determines whether to normalize input data using MinMaxScaler, which adjusts feature scales to a common range.
     - True
     - [True, False]
   * - :py:data:`verbose`
     - Controls whether to display execution details in the terminal, useful for debugging or understanding the method's operation.
     - False
     - [True, False]
   * - :py:data:`pixel_width`
     - Sets the width of each bar in the image representation, influencing the visual density of the bars.
     - 1
     - integer > 0
   * - :py:data:`gap`
     - Defines the gap between bars in pixels, affecting the separation and visual clarity between individual data representations.
     - 0
     - integer >= 0
   * - :py:data:`zoom`
     - Adjusts the multiplication factor for scaling the image relative to its original size, enhancing visibility or detail for large datasets.
     - 1
     - integer > 0




Code example:

>>> model = BarGraph(problem='regression')

All the parameters that aren't expecifically setted will have their default values.

Functions
---------
BarGraph has the following functions:

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
**Paper**: https://doi.org/10.1038/s41598-022-26378-6

**Code Repository**: https://github.com/anuraganands/Non-image-data-classification-with-CNN

