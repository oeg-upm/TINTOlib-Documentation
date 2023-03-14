Installation
=====

.. _installation:

Installation
------------

To use Data2Image, first install it using `PyPi <https://pypi.org/project/tintonera-prueba/>`_:

.. code-block:: console

   (.venv) $ pip install tintonera-prueba

Import methods
----------------
Data2Image contains state-of-the-art most important methods for the construction of Synthetic Images from Sorted Data (also known as Tabular Data). All the methods requires the same input format and the responses outputs will have the same format.

>>> from tinto_prueba.methods import tinto


Input Format
------------
To import the Tabular Data there are 2 options:

* Use raw CSV path
* Use Pandas Dataframe instance with the data

Output Format
-------------
The output of the model.generateImages() method are synthetic images grouped in folders depending on their class value. 

For example: 

If the dataset is composed of 3 different classes, the model.generateImages() method will create 3 folders and each folder will contain one synthetic image for each instance with that class. 

