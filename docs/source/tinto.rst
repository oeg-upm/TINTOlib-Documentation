TINTO
=====

Hyperparameters & Configuration
---------------
.. list-table:: 
   :widths: 20 40 20 20
   :header-rows: 1

   * - :py:data:`algorithm`
     - Dimensionality reduction algorithm
     - PCA
     - [PCA, t-SNE]
   * - :py:data:`pixels`
     - Image's Pixels (one side)
     - 20
     - integer
   * - :py:data:`blur`
     - Active option blurring
     - False
     - [True, False]
   * - :py:data:`amplification`
     - Amplification in blurring
     - :py:data:`np.pi`
     - float
   * - :py:data:`distance`
     - Distance in blurring (number of pixels)
     - 2
     - integer
   * - :py:data:`steps`
     - Steps in blurring
     - 4
     - integer
   * - :py:data:`option`
     - Option in blurring
     - mean
     - [mean, maximum]
   * - :py:data:`seed`
     - Seed
     - 20
     - integer
   * - :py:data:`times`
     - Times replication in t-SNE
     - 4
     - integer
   * - :py:data:`verbose`
     - Verbose: if it's true, show the compilation text
     - False
     - [True, False]

  
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

