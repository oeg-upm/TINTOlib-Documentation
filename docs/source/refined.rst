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
     -  The type of problem, this will define how the images are grouped.
     -  'supervised'
     - ['supervised', 'unsupervised', 'regression']
   * - :py:data:`n_processors`
     -  The number of processors to use for the algorithm. It must be an integer greater than or equal to 2.
     -  '8'
     - int
   * - :py:data:`hcIterations`
     -  Number of iterations of the hill climbing algorithm.
     -  '5'
     - int
   * - :py:data:`zoom`
     - Multiplication factor that determines the size of the saved image relative to the original size. Values greater than 1 will increase the size of the saved image proportionally.
     - 1
     - int
   * - :py:data:`random_seed`
     - Seed for reproducibility.
     - 1
     - integer
   * - :py:data:`verbose`
     - Show in terminal the execution.
     - False
     - [True, False]




Code example:

>>> model = REFINED(problem='regression')

All the parameters that aren't expecifically setted will have their default values.

Functions
---------

.. list-table::
   :widths: 20 60 20
   :header-rows: 1

   * - Function
     - Description
     - Output
   * - :py:data:`saveHyperparameters(filename)`
     -  Allows to save the defined parameters ().
     -  .pkl file with the configuration
   * - :py:data:`loadHyperparameters(filename)`
     - Load SuperTML configuration previously saved with :py:data:`saveHyperparameters(filename)`

        - filename: .pkl file path
     -
   * - :py:data:`generateImages_fit(data, folder)`
     - Fits the model and generates one synthetic image per instance, organizing them into folders grouped by class

        - data: Path to the CSV file or a pandas DataFrame containing the input data
        - folder: Path to the destination folder where the generated images will be saved
     - Folders with synthetic images
   * - :py:data:`generateImages_pred(data, folder)`
     - Generates one synthetic image per instance without fitting a model, organizing them into folders grouped by class

        - data: Path to the CSV file or a pandas DataFrame containing the input data
        - folder: Path to the destination folder where the generated images will be saved
     - Folders with synthetic images




Citation
------
**Paper**: https://www.nature.com/articles/s41467-020-18197-y

**Code Repository**: https://github.com/omidbazgirTTU/REFINED

