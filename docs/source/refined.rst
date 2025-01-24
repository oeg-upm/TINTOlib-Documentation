REFINED
=====

Import REFINED
----------------
To import REFINED model use:

>>> from TINTOlib.refined import REFINED
>>> model = REFINED()

Hyperparameters & Configuration
---------------

When creating the :py:class:`REFINED` class, some parameters can be modified. The parameters are:


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
   * - :py:data:`hcIterations`
     - Number of iterations for the hill climbing algorithm.
     - 5
     - integer >= 1
   * - :py:data:`n_processors`
     - The number of processors to use for the algorithm.
     - 8
     - integer >= 2
   * - :py:data:`zoom`
     - Multiplication factor determining the size of the saved image relative to the original size.
     - 1
     - integer > 0
   * - :py:data:`random_seed`
     - Seed for reproducibility.
     - 1
     - integer




Code example:

>>> model = REFINED(problem='regression')

All the parameters that aren't expecifically setted will have their default values.

Functions
---------
REFINED has the following functions:

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
**Paper**: https://doi.org/10.1038/s41467-020-18197-y

**Code Repository**: https://github.com/omidbazgirTTU/REFINED

