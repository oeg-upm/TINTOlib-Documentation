IGTD
=====

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
     -  The type of problem, this will define how the images are grouped.
     -  'supervised'
     - ['supervised', 'unsupervised', 'regression']
   * - :py:data:`scale`
     - Characteristic pixels of the final image (row x col). [row x col] must be equal or greater than the number of features.
     - [6,6]
     - [int, int]
   * - :py:data:`zoom`
     - Multiplication factor that determines the size of the saved image relative to the original figure size. Values greater than 1 will increase the size of the saved image proportionally using Nearest-neighbor interpolation.
     - 1
     - int
   * - :py:data:`fea_dist_method`
     - Correlation coefficient to evaluate similarity between features.
     - 'Pearson'
     - ['Pearson', 'Spearman', 'set', 'Euclidean']
   * - :py:data:`image_dist_method`
     - Method used to calculate distance.
     - 'Euclidean'
     - ['Euclidean', 'Manhattan']
   * - :py:data:`max_step`
     - The maximum steps that the algorithm should run if never converges.
     - 1000
     - int
   * - :py:data:`val_step`
     - Number of steps for checking gain on the objective function to determine convergence.
     - 50
     - int
   * - :py:data:`error`
     - Function to evaluate the difference between feature distance ranking and pixel distance ranking.
     - 'squared'
     - ['squared', 'abs']
   * - :py:data:`switch_t`
     - The threshold to determine whether switch should happen.
     - 0
     - int
   * - :py:data:`min_gain`
     - If the objective function is not improved more than 'min_gain' in 'val_step' steps, the algorithm terminates.
     - 0.00001
     - float
   * - :py:data:`random_seed`
     - Seed for reproducibility.
     - 1
     - integer
   * - :py:data:`verbose`
     - Show in terminal the execution.
     - False
     - [True, False]




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
     -  Allows to save the defined parameters (scale, fea_dist_method, image_dist_method....).
     -  .pkl file with the configuration
   * - :py:data:`loadHyperparameters(filename)`
     - Load IGTD configuration previously saved with :py:data:`saveHyperparameters(filename)`

        - filename: .pkl file path
     -
   * - :py:data:`generateImages(data, folder)`
     - Generate one image per instance and group by class in different folder

        - data: path of the CSV or pandas dataframe
        - folder: path of the folder to save results
     - Folders with synthetic images






Citation
------
**Paper**: https://doi.org/10.1038/s41598-021-90923-y

**Code Repository**: https://github.com/zhuyitan/igtd
