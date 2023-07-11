Refined
=====

Import Refined
----------------
To import Refined model use:

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
   * - :py:data:`hcIterations`
     - Maximum number of iterations of the hill climbing algorithm
     - 100
     - integer
   * - :py:data:`verbose`
     - Show in terminal the execution
     - False
     - boolean




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
   * - :py:data:`generateImages(data, folder)`
     - Generate one image per instance and group by class in different folder

        - data: path of the CSV or pandas dataframe
        - folder: path of the folder to save results
     - Folders with synthetic images




Citation
------
**Paper**: https://doi.org/10.1038/s41467-020-18197-y

**Code Repository**: https://github.com/omidbazgirTTU/REFINED

