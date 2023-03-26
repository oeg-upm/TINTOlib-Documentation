TINTO
=====

Import SuperTML
----------------
To import TINTO model use:

>>> from data2Image.models import SuperTML
>>> model = SuperTML()

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
     - Allows to save the defined parameters .
     - .pkl file with the configuration

   * - :py:data:`loadHyperparameters(filename)`
     - Load TINTO configuration previously saved with :py:data:`saveHyperparameters(filename)`

        - filename: .pkl file path
   * - :py:data:`generateImages(data, folder)`
     - Generate one image per instance and group by class in different folder

        - data: path of the CSV or pandas dataframe
        - folder: path of the folder to save results
     - Folders with synthetic images



Citation
------
**Paper**: https://doi.org/10.1016/j.inffus.2022.10.011

**Code Repository**: https://github.com/oeg-upm/TINTO

