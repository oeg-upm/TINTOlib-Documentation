Introduction
=====

.. _installation:

Installation
------------

To use Data2Image, first install it using `PyPi <https://pypi.org/project/tintonera-prueba/>`_:

.. code-block:: console

   (.venv) $ pip install tintonera-prueba

Import methods
----------------
Data2Image contains state-of-the-art most important methods for the construction of Synthetic Images from Sorted Data (also known as Tabular Data). The following code can be used to import the desired model:

>>> from tinto_prueba.methods import tinto


All the methods requires the same input format and the responses outputs will have the same format.

Available Models
--------------
.. list-table:: 
   :widths: 25 25 50
   :header-rows: 1

   * - Method
     - Import class
     - Features
   * - TINTO
     - tinto
     - blur
     
Input Format
------------
To import the Tabular Data there are 2 options:


Raw CSV path
#######
Raw CSV path can be used with X method . The CSV file must have the following format:

* Data must be in CSV with the default separator, i.e., commas.
* Only create images when we have data for a binary or multi-class classification problem.
* The last column should be the targer (variable to predict).
* The first columns will be the characteristics.
* All variables must be in numerical format.
* The script takes by default the first row as the name of each feature, therefore, the different features must be named.
* Each sample (row) of the dataset will correspond to an image.


Pandas Dataframe
###############
* Developing:

    .. code-block:: bash

      Example code


Output Format
-------------
The output of the :py:func:`model.generateImages()` method are synthetic images grouped in folders depending on their class value. 

For example: 

If the dataset is composed of 3 different classes, the :py:func:`model.generateImages()` method will create 3 folders and each folder will contain one synthetic image for each instance with that class. 

