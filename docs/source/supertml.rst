SuperTML
=====

The SuperTML method transforms tabular data into images by drawing data values directly onto a single-channel (black and white) image. Each feature is assigned a specific region on the image, depicted either as text or a numerical representation. SuperTML offers two distinct variations:

1. **SuperTML_EF (Equal Font)**:
   - This approach assigns equally sized regions for each feature and uses a uniform font size across the image, ensuring that all features are treated equally in terms of visual representation.

2. **SuperTML_VF (Variable Font)**:
   - In this variation, the size of the region and the font size are adjusted based on the feature's importance. More significant features receive larger regions and font sizes, highlighting key features more prominently.


.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/SuperTML-EF_005854_zoom.png
   :width: 100px
   :align: center
   :alt: Synthetic image generated using the SuperTML-EF method, featuring uniform font size for all features.


Import SuperTML
----------------
To import SuperTML model use:

>>> from TINTOlib.supertml import SuperTML
>>> model = SuperTML()

Hyperparameters & Configuration
---------------

When creating the :py:class:`SuperTML` class, some parameters can be modified. The parameters are:


.. list-table::
   :widths: 20 40 20 20
   :header-rows: 1

   * - Parameters
     - Description
     - Default value
     - Valid values
   * - :py:data:`problem`
     - The type of problem, defining how the images are grouped.
     - 'supervised'
     - ['supervised', 'unsupervised', 'regression']
   * - :py:data:`normalize`
     - If True, normalizes input data using MinMaxScaler.
     - True
     - [True, False]
   * - :py:data:`verbose`
     - Show execution details in the terminal.
     - False
     - [True, False]
   * - :py:data:`image_pixels`
     - The number of pixels used to create the image (one side), total pixels = pixels * pixels.
     - 224
     - integer
   * - :py:data:`feature_importance`
     - If False, SuperTML-EF (Equal Font) is used, where all features are displayed with equal font sizes. If True, SuperTML-VF (Variable Font) is used, where the font size of each feature is proportional to its importance.
     - False
     - [True, False]
   * - :py:data:`font_size`
     - The size of the font used to render text on the generated images.
     - 10
     - integer
   * - :py:data:`random_seed`
     - Seed for reproducibility; the method uses random forest for feature importance.
     - 1
     - integer




Code example:

>>> model = SuperTML(problem='regression')

All the parameters that aren't expecifically setted will have their default values.

Functions
---------
SuperTML has the following functions:

.. list-table::
   :widths: 20 60 20
   :header-rows: 1

   * - Function
     - Description
     - Output
   * - :py:data:`saveHyperparameters(filename)`
     - Allows to save the defined parameters (scale, fea_dost_method, image_dist_method, etc.)
     - .pkl file with the configuration
   * - :py:data:`loadHyperparameters(filename)`
     - Load TINTO configuration previously saved with :py:data:`saveHyperparameters(filename)`

        - filename: .pkl file path
     -
   * - :py:data:`fit(data)`
     - Trains the model on the tabular data and prepares it for image generation.

        - data: A path to a CSV file or a Pandas DataFrame containing the features and targets. The target column must be the last column.
     -
   * - :py:data:`transform(data, folder)`
     - Generates and saves synthetic images in a specified folder. Requires the model to be fitted first.

        - data: A path to a CSV file or a Pandas DataFrame containing the features and targets. The target column must be the last column.
        - folder: Path to the folder where the synthetic images will be saved.
     - Folders with synthetic images
   * - :py:data:`fit_transform(data, folder)`
     - Combines the training and image generation steps. Fits the model to the data and generates synthetic images in one step.

        - data: A path to a CSV file or a Pandas DataFrame containing the features and targets. The target column must be the last column.
        - folder: Path to the folder where the synthetic images will be saved.
     - Folders with synthetic images

- **The model must be fitted** before using the `transform` method. If the model isn't fitted, a `RuntimeError` will be raised.





Citation
------
**Paper**: https://doi.ieeecomputersociety.org/10.1109/CVPRW.2019.00360

**Code Repository**: https://github.com/GilesStrong/SuperTML_HiggsML_Test

