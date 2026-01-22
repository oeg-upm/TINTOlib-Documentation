SuperTML
========

The SuperTML method transforms tabular data into synthetic images by drawing data values directly onto a 3-channel (RGB) image. Each feature is assigned a specific region on the image, depicted as text representing the numerical value. SuperTML offers two distinct variations:

1. **SuperTML_EF (Equal Font)**:
   - This approach assigns equally sized regions for each feature and uses a uniform font size across the image, ensuring that all features are treated equally in terms of visual representation.

2. **SuperTML_VF (Variable Font)**:
   - In this variation, the size of the region and the font size are adjusted based on the feature's importance (calculated via Random Forest). More significant features receive larger regions and font sizes, highlighting key features more prominently.

.. image:: https://raw.githubusercontent.com/oeg-upm/TINTOlib-Documentation/refs/heads/main/assets/Synthetic-images/SuperTML-EF_005854_zoom.png
   :width: 200px
   :align: center
   :alt: Synthetic image generated using the SuperTML-EF method, featuring uniform font size for all features.

Import SuperTML
---------------
To import SuperTML model use:

>>> from TINTOlib.supertml import SuperTML
>>> model = SuperTML()

⚠️ Font Requirements
--------------------

SuperTML generates text-based synthetic images and strictly requires the **Arial** font (`arial.ttf`) for correct rendering.

- On **Windows**, this font is typically available by default.
- On **Linux** and **macOS**, it must be installed manually if not present to avoid `OSError: cannot open resource` when generating images.

To ensure the font is available:

**Linux**

Install the Microsoft Core Fonts:

.. code-block:: bash

   sudo apt install ttf-mscorefonts-installer

**macOS**

Use Homebrew to install the fonts:

.. code-block:: bash

   brew tap homebrew/cask-fonts
   brew install --cask font-arial

**Google Colab**

On **Google Colab**, you may need to upload `arial.ttf` to the working directory or install the font package, as it is not always available by default.

Hyperparameters & Configuration
-------------------------------

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
     - 'classification'
     - ['classification', 'unsupervised', 'regression']
   * - :py:data:`transformer`
     - Preprocessing transformations like scaling, normalization, etc.
     - MinMaxScaler()
     - Scikit Learn transformers or custom implementation inheriting CustomTransformer.
   * - :py:data:`verbose`
     - Show execution details in the terminal.
     - False
     - [True, False]
   * - :py:data:`pixels`
     - The number of pixels used to create the image (one side). Total pixels = pixels * pixels.
     - 224
     - integer
   * - :py:data:`feature_importance`
     - If False, SuperTML-EF (Equal Font) is used. If True, SuperTML-VF (Variable Font) is used, scaling font size by feature importance.
     - False
     - [True, False]
   * - :py:data:`font_size`
     - The base size of the font used to render text on the generated images.
     - 10
     - integer
   * - :py:data:`random_seed`
     - Seed for reproducibility.
     - 1
     - integer

Code example:

>>> model = SuperTML(problem='regression', feature_importance=True, pixels=224, font_size=12)

All the parameters that aren't specifically set will have their default values.

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
     - Load SuperTML configuration previously saved with :py:data:`saveHyperparameters(filename)`

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
--------
**Paper**: https://doi.ieeecomputersociety.org/10.1109/CVPRW.2019.00360

**Code Repository**: https://github.com/GilesStrong/SuperTML_HiggsML_Test