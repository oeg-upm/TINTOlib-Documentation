FeatureWrap
=====

Import FeatureWrap
----------------
To import FeatureWrap model use:

>>> from TINTOlib.featureWrap import FeatureWrap
>>> model = FeatureWrap()

Hyperparameters & Configuration
---------------

When creating the :py:class:`FeatureWrap` class, some parameters can be modified. The parameters are:


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
   * - :py:data:`size`
     - The width and height of the final image, in pixels (rows x columns).
     - [8,8]
     - [int, int]
   * - :py:data:`bins`
     - The number of bins or intervals used for grouping numeric data
     - 10
     - int
   * - :py:data:`zoom`
     - Multiplication factor that determines the size of the saved image relative to the original size. Values greater than 1 will increase the size of the saved image proportionally.
     - 1
     - int
   * - :py:data:`verbose`
     - Show in terminal the execution.
     - False
     - [True, False]




Code example:

>>> model = FeatureWrap(size=[10,10], bins=20)

All the parameters that aren't expecifically setted will have their default values.

Functions
---------
FeatureWrap has the following functions:

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
     - Load FeatureWrap configuration previously saved with :py:data:`saveHyperparameters(filename)`

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
**Paper**: https://doi.org/10.1007/978-3-319-70139-4_87

**Code Repository**: 
