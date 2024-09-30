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
     -  The type of problem, this will define how the images are grouped.
     -  'supervised'
     - ['supervised', 'unsupervised', 'regression']
   * - :py:data:`zoom`
     - Scaling factor for the output images.
     - 1
     - int
   * - :py:data:`verbose`
     - Show in terminal the execution.
     - False
     - [True, False]




Code example:

>>> model = Combination(problem='regression')

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
     - Load Combination configuration previously saved with :py:data:`saveHyperparameters(filename)`

        - filename: .pkl file path
     -
   * - :py:data:`generateImages(data, folder)`
     - Generate one image per instance and group by class in different folder

        - data: path of the CSV or pandas dataframe
        - folder: path of the folder to save results
     - Folders with synthetic images




Citation
------
**Paper**:

**Code Repository**:

