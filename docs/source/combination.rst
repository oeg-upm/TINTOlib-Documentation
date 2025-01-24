Combination
=====

Import Combination
----------------
To import Combination model use:

>>> from TINTOlib.combination import Combination
>>> model = Combination()

Hyperparameters & Configuration
---------------

When creating the :py:class:`Combination` class, some parameters can be modified. The parameters are:


.. list-table::
   :widths: 20 40 20 20
   :header-rows: 1

   * - Parameters
     - Description
     - Default value
     - Valid values
   * - :py:data:`problem`
     - Specifies how images are grouped according to the type of problem, affecting how data is visualized.
     - 'supervised'
     - ['supervised', 'unsupervised', 'regression']
   * - :py:data:`normalize`
     - Determines whether to normalize input data using MinMaxScaler, essential for maintaining consistent feature scales across different data transformations.
     - True
     - [True, False]
   * - :py:data:`verbose`
     - Enables display of detailed execution processes in the terminal, useful for monitoring method operations and troubleshooting.
     - False
     - [True, False]
   * - :py:data:`zoom`
     - Adjusts the multiplication factor for scaling the output image relative to its original dimensions, enhancing the visual presentation of data.
     - 1
     - integer > 0




Code example:

>>> model = Combination(problem='regression')

All the parameters that aren't expecifically setted will have their default values.

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

