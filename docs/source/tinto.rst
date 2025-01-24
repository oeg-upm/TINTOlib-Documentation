TINTO
=====

Import TINTO
----------------
To import TINTO model use:

>>> from TINTOlib.tinto import TINTO
>>> model = TINTO()

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
   * - :py:data:`problem`
     -  The type of problem, this will define how the images are grouped.
     -  'supervised'
     - ['supervised', 'unsupervised', 'regression']
   * - :py:data:`algorithm`
     - Select the dimensionality reduction algorithm.
     - PCA
     - [PCA, t-SNE]
   * - :py:data:`pixels`
     - The number of pixels used to create the image (only one side, total_pixels = pixels * pixels).
     - 20
     - integer
   * - :py:data:`submatrix`
     - Specifies whether to use a submatrix for blurring.
     - True
     - [True, False]
   * - :py:data:`blur`
     - Activate or deactivate the blurring option.
     - False
     - [True, False]
   * - :py:data:`amplification`
     - Only with :py:data:`blur=true`, blurring amplification.
     - :py:data:`np.pi`
     - float
   * - :py:data:`distance`
     - Only with :py:data:`blur=true`, blurring distance (number of pixels).
     - 2
     - integer
   * - :py:data:`steps`
     - Only with :py:data:`blur=true`, blurring steps.
     - 4
     - integer
   * - :py:data:`option`
     - Only with :py:data:`blur=true`, technique for handling overlapping pixels.
     - mean
     - [mean, maximum]
   * - :py:data:`times`
     - Only with :py:data:`algorithm=t-SNE`, times replication in t-SNE.
     - 4
     - integer
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

>>> model = TINTO(algorithm="t-SNE",pixels=30,blur=True,option="maximum")

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
     -  Allows to save the defined parameters (scale, fea_dost_method, image_dist_method....)
     -  .pkl file with the configuration
   * - :py:data:`loadHyperparameters(filename)`
     - Load TINTO configuration previously saved with :py:data:`saveHyperparameters(filename)`

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
**Paper**: https://doi.org/10.1016/j.inffus.2022.10.011

**Code Repository**: https://github.com/oeg-upm/TINTO

