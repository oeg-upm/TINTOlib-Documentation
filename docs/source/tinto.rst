TINTO
=====

Import TINTO
----------------
To import TINTO model use:

>>> from tinto_prueba.methods import tinto
>>> model = tinto()

Hyperparameters & Configuration
---------------

When creating the :py:class:`tinto` class, some parameters can be modified. The parameters are:


.. list-table:: 
   :widths: 20 40 20 20
   :header-rows: 1

   * - Parameters
     - Description
     - Default value
     - Valid values
   * - :py:data:`algorithm`
     - Select the dimensionality reduction algorithm between the options
     - PCA
     - [PCA, t-SNE]
   * - :py:data:`pixels`
     - The number of pixels used to create the image (only one side, total_pixels = pixels * pixels)
     - 20
     - integer
   * - :py:data:`blur`
     - Activate or deactivate the blurring option
     - False
     - [True, False]
   * - :py:data:`amplification`
     - Only with :py:data:`blur=true`, blurring amplification
     - :py:data:`np.pi`
     - float
   * - :py:data:`distance`
     - Only with :py:data:`blur=true`, blurring distance (number of pixels)
     - 2
     - integer
   * - :py:data:`steps`
     - Only with :py:data:`blur=true`, blurring steps
     - 4
     - integer
   * - :py:data:`option`
     - Only with :py:data:`blur=true`, technique for handling overlapping pixels
     - mean
     - [mean, maximum]
   * - :py:data:`seed`
     - Seed for the random numbers used in the method
     - 20
     - integer
   * - :py:data:`times`
     - Only with :py:data:`algorithm=t-SNE`, times replication in t-SNE
     - 4
     - integer
   * - :py:data:`verbose`
     - Show in terminal the execution
     - False
     - [True, False]




Code example:

>>> model = tinto(algorithm="t-SNE",pixels=30,blur=True,option="maximum")

All the parameters that aren't expecifically setted will have their default values.

Functions
---------
.. list-table:: 
   :widths: 20 40 20 
   :header-rows: 1

   * - Function
     - Description
     - Output
     
   * - :py:data:`saveHyperparameters(filename)`
     - Allows to save the defined parameters (algorithm, pixels, blur....). 
     - .pkl file with the configuration

   * - :py:data:`loadHyperparameters(filename)`
     - Load TINTO configuration previously saved with :py:data:`saveHyperparameters(filename)`
        - filename: .pkl file path
     -
   * - :py:data:`generateImages(data, folder)`
     - Generate one image per instance and group by class in different folder
        - data: path of the CSV or pandas dataframe
        - folder: path of the folder to save results
     - Folders with synthetic images



Citation
------
**Paper**: https://doi.org/10.1016/j.inffus.2022.10.011

**Code Repository**: https://github.com/oeg-upm/TINTO

