Clusters
========

The Clusters method transforms tabular data into synthetic grayscale or multi-channel images by first learning a latent representation with clustering- or density-based unsupervised techniques, and then reshaping that representation into square image matrices.

Import Clusters
---------------
To import Clusters model use:

>>> from TINTOlib.clusters import Clusters
>>> model = Clusters()

Hyperparameters & Configuration
-------------------------------

When creating the :py:class:`Clusters` class, some parameters can be modified. The parameters are:

.. list-table::
   :widths: 20 40 10 10 20
   :header-rows: 1

   * - Parameters
     - Description
     - Default value
     - Algorithm
     - Valid values
   * - :py:data:`problem`
     - The type of problem, defining how the images are grouped.
     - None
     - All
     - ['classification', 'unsupervised', 'regression']
   * - :py:data:`normalize`
     - Parameter kept in the constructor for API compatibility. In this implementation it is accepted as input, but it is not used in the call to the parent class constructor.
     - None
     - All
     - [True, False]
   * - :py:data:`verbose`
     - Show execution details in the terminal.
     - None
     - All
     - [True, False]
   * - :py:data:`algorithm`
     - Algorithm / technique used to generate the latent representation that is later converted into an image.
     - 'kmeans'
     - All
     - ['kmeans', 'gaussianMix', 'aggloKNN', 'mixMethod', 'kde', 'kmedoids', 'factor']
   * - :py:data:`n_clusters`
     - Number of clusters or latent components used to represent the data. The image side is computed from the square root of this value, rounded up when necessary. It can also be ``'auto'`` or a list of candidate integers for automatic selection based on SSIM stability. This option is not available for ``kde`` or ``aggloKNN``.
     - 16
     - ['kmeans', 'gaussianMix', 'aggloKNN', 'mixMethod', 'kmedoids', 'factor']
     - integer, ``'auto'``, or list of integers
   * - :py:data:`random_seed`
     - Seed for reproducibility.
     - 1
     - All
     - integer
   * - :py:data:`n_init`
     - Number of initializations for the ``kmeans`` and ``gaussianMix`` algorithms.
     - 'auto'
     - ['kmeans', 'gaussianMix', 'mixMethod']
     - integer or 'auto'
   * - :py:data:`max_iter`
     - Maximum number of iterations for ``kmeans``, ``gaussianMix``, and ``kmedoids``.
     - 300
     - ['kmeans', 'gaussianMix', 'mixMethod', 'kmedoids']
     - integer
   * - :py:data:`algorithmMethod`
     - Variant of the k-means algorithm used by ``kmeans``.
     - 'lloyd'
     - ['kmeans', 'mixMethod']
     - ['lloyd', 'elkan']
   * - :py:data:`covariance_type`
     - Covariance type used by the Gaussian Mixture model.
     - 'full'
     - ['gaussianMix', 'mixMethod']
     - ['full', 'tied', 'diag', 'spherical']
   * - :py:data:`ensamMethod`
     - List of methods used when ``algorithm='mixMethod'``. Each method corresponds to one image channel. Methods cannot be repeated and the list length must be between 1 and 3.
     - []
     - ['mixMethod']
     - ['kmeans', 'gaussianMix', 'aggloKNN', 'kmedoids', 'factor']
   * - :py:data:`bandwidth`
     - Bandwidth used in kernel density estimation.
     - 1.0
     - ['kde']
     - float
   * - :py:data:`kernel`
     - Kernel type used by the KDE algorithm.
     - 'gaussian'
     - ['kde']
     - ['gaussian', 'tophat', 'epanechnikov', 'exponential', 'linear', 'cosine']
   * - :py:data:`metric`
     - Distance metric used by ``aggloKNN``, ``kmedoids``, and ``kde``. The valid values depend on the selected algorithm. When ``'manhattan'`` is provided, it is internally converted to ``'cityblock'``.
     - 'euclidean'
     - ['kde', 'aggloKNN', 'kmedoids', 'mixMethod']
     - For ``kmedoids`` and ``kde``: ['euclidean', 'manhattan', 'chebyshev']; for ``aggloKNN``: ['euclidean', 'manhattan', 'cosine']; for ``mixMethod``: ['euclidean', 'manhattan']
   * - :py:data:`RBFKmeans`
     - If True, transforms the distances to k-means centroids with an RBF function before image generation.
     - False
     - ['kmeans', 'mixMethod']
     - [True, False]

Code example:

>>> model = Clusters(
...     problem='classification',
...     algorithm='kmeans',
...     n_clusters=25,
...     random_seed=1,
...     max_iter=300,
...     RBFKmeans=True
... )

All the parameters that aren't specifically set will have their default values.

Algorithm Notes
---------------

The class supports several internal strategies to build the representation that is later reshaped into an image:

- ``kmeans``:
  
  Uses the distances from each sample to the cluster centroids. Optionally, these distances can be transformed with an RBF kernel before image generation.

- ``gaussianMix``:
  
  Uses the posterior probabilities returned by a Gaussian Mixture Model.

- ``aggloKNN``:
  
  First applies Agglomerative Clustering with a k-nearest-neighbors connectivity graph, and then trains a KNN classifier on the resulting pseudo-labels to obtain class probabilities.

- ``kde``:
  
  Estimates a one-dimensional kernel density distribution for each feature and uses the density values as the transformed representation.

- ``kmedoids``:
  
  Uses distances from each sample to the learned medoids obtained through a PAM-like procedure.

- ``factor``:
  
  Uses the latent representation obtained from Factor Analysis.

- ``mixMethod``:
  
  Combines up to three different methods into a 3-channel image. Each selected method fills one channel.

Additional constraints:

- ``mixMethod`` requires ``ensamMethod`` to contain between 1 and 3 non-repeated methods.
- ``kde`` and ``aggloKNN`` do not support automatic cluster selection with ``n_clusters='auto'`` or a list of candidate values.
- If ``factor`` is used, the number of clusters/components must be smaller than the number of features minus one.
- In grayscale mode, ``kmeans`` and ``kmedoids`` reorder the transformed features according to centroid/medoid proximity before reshaping them into the image.
- In multi-channel mode, if fewer than three channels are provided, the remaining channels are filled with zeros.

Functions
---------
Clusters has the following functions:

.. list-table::
   :widths: 20 60 20
   :header-rows: 1

   * - Function
     - Description
     - Output
   * - :py:data:`saveHyperparameters(filename)`
     - Allows to save the defined parameters.
     - .pkl file with the configuration
   * - :py:data:`loadHyperparameters(filename)`
     - Load Clusters configuration previously saved with :py:data:`saveHyperparameters(filename)`

       - filename: .pkl file path
     -
   * - :py:data:`fit(data)`
     - Trains the model on the tabular data. Depending on the selected algorithm, this step learns centroids, medoids, Gaussian mixture components, factor projections, KDE distributions, or multi-channel representations.

       - data: A path to a CSV file or a Pandas DataFrame containing the features and targets. The target column must be the last column.
     -
   * - :py:data:`transform(data, folder)`
     - Generates and saves synthetic images in a specified folder using the representation learned during fitting.

       - data: A path to a CSV file or a Pandas DataFrame containing the features and targets. The target column must be the last column.
       - folder: Path to the folder where the synthetic images will be saved.
     - Folders with synthetic images
   * - :py:data:`fit_transform(data, folder)`
     - Combines the training and image generation steps. Fits the model to the data and generates synthetic images in one step.

       - data: A path to a CSV file or a Pandas DataFrame containing the features and targets. The target column must be the last column.
       - folder: Path to the folder where the synthetic images will be saved.
     - Folders with synthetic images

- **The model must be fitted** before using the ``transform`` method. If the model isn't fitted, a ``RuntimeError`` will be raised.
