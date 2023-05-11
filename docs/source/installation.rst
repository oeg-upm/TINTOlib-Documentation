Introduction
=====

.. _installation:

Installation
------------

To use TINTOlib, first install it using `PyPi <https://pypi.org/project/TINTOlib>`_:

.. code-block:: console

   (.venv) $ pip install TINTOlib

Import methods
----------------
TINTOlib contains state-of-the-art most important methods for the construction of Synthetic Images from Sorted Data (also known as Tabular Data). The following code can be used to import the desired model:

>>> from TINTOlib.tinto import TINTO


All the methods requires the same input format and the responses outputs will have the same format.

Available Models
--------------
.. list-table:: 
   :widths: 50 50 50 50
   :header-rows: 1

   * - Method
     - Class name
     - Features
     - Hyperparameters
   * - TINTO
     - TINTO()
     - blur
     - `algorithm`, `pixels`, `blur`, `amplification`, `distance`, `steps`, `option`, `seed`, `times`, `verbose`
   * - SuperTML
     - SuperTML()
     -
     - `problem`, `verbose`
   * - IGTD
     - IGTD()
     -
     -  `problem`, `scale`, `fea_dost_method`, `save_image_size`, `max_step`, `val_step`, `error`, `switch_t`, `min_gain`, `seed`, `verbose`

Input Format
------------
To import the Tabular Data there are 2 options:


Raw CSV path
#######
The CSV file must have the following format:

* Data must be in CSV with the default separator, i.e., commas.
* Only create images when we have data for a binary or multi-class classification problem.
* The last column should be the targer (variable to predict).
* The first columns will be the characteristics.
* All variables must be in numerical format.
* The script takes by default the first row as the name of each feature, therefore, the different features must be named.
* Each sample (row) of the dataset will correspond to an image.

Code example
    .. code-block:: bash


      model=TINTO()
      model.generateImages(CsvPath,resultFolderPath)
Pandas Dataframe
###############
Pandas dataframe format can be also used to load the data:

Code example
    .. code-block:: bash

      pandasDf=pd.read_csv(dataPath)
      model=TINTO()
      model.generateImages(pandasDf,resultFolderPath)


Output Format
-------------
The output of the :py:func:`model.generateImages(data,folder)` method are synthetic images grouped in folders depending on their class value.

For example: 

If the dataset is composed of 3 different classes, the :py:func:`model.generateImages(data,folder)` method will create 3 folders and each folder will contain one synthetic image for each instance with that class.

