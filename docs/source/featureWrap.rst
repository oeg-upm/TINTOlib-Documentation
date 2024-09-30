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
     - Scaling factor for the output images.
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
   * - :py:data:`generateImages(data, folder)`
     - Generate one image per instance and group by class in different folder

        - data: path of the CSV or pandas dataframe
        - folder: path of the folder to save results
     - Folders with synthetic images






Citation
------
**Paper**: https://doi.org/10.1007/978-3-319-70139-4_87

**Code Repository**: 
