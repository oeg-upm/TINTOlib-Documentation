SuperTML
=====

Import SuperTML
----------------
To import SuperTML model use:

>>> from TINTOlib.supertml import SuperTML
>>> model = SuperTML()

Hyperparameters & Configuration
---------------

When creating the :py:class:`SuperTML` class, some parameters can be modified. The parameters are:


.. list-table:: 
   :widths: 20 5 20 20
   :header-rows: 1

   * - Parameters
     - Description
     - Default value
     - Valid values
   * - :py:data:`problem`
     - The type of problem, this will define how the images are grouped.
     - 'supervised'
     - ['supervised', 'unsupervised', 'regression']
   * - :py:data:`image_pixels`
     - The number of pixels used to create the image (only one side, total_pixels = pixels * pixels).
     - 224
     - integer
   * - :py:data:`feature_importance`
     - If False, SuperTML-EF (Equal Font) is used, where all features are displayed with equal font sizes. If True, SuperTML-VF (Variable Font) is used, where the font size of each feature is proportional to its importance.
     - False
     - [True, False]
   * - :py:data:`font_size`
     - The size of the font used to render the text on the generated images.
     - 10
     - integer
   * - :py:data:`random_seed`
     - Seed for reproducibility.
     - 1
     - integer
   * - :py:data:`verbose`
     - Show in terminal the execution.
     - False
     - [True, False]




Code example:

>>> model = SuperTML(problem='regression')

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
**Paper**: https://doi.ieeecomputersociety.org/10.1109/CVPRW.2019.00360

**Code Repository**: https://github.com/GilesStrong/SuperTML_HiggsML_Test

