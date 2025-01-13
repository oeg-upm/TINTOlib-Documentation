BIE
=====

Import BIE
----------------
To import the BIE model, use:

>>> from TINTOlib.bie import BIE
>>> model = BIE()

Hyperparameters & Configuration
---------------

When creating the :py:class:`BIE` class, some parameters can be modified. The parameters are:


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
   * - :py:data:`precision`
     - Number of bits used to represent each feature.
     - 32
     - [32, 64]
   * - :py:data:`zoom`
     - Multiplication factor that determines the size of the saved image relative to the original size. Values greater than 1 will increase the size of the saved image proportionally.
     - 1
     - Positive integer
   * - :py:data:`verbose`
     - Show in terminal the execution.
     - False
     - [True, False]




Code example:

>>> model = BIE(problem='regression', precision=64, zoom=2)

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
     - Load BIE configuration previously saved with :py:data:`saveHyperparameters(filename)`

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
**Paper**: https://ieeexplore.ieee.org/document/10278393

**Code Repository**: https://jds-online.org/journal/JDS/article/1360/file/12976

