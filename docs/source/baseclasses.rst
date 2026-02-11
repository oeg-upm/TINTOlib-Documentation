Base classes
============

This section documents the abstract base classes that provide shared behavior
across TINTOlib methods, following a scikit-learn style layout.

Inheritance overview
--------------------

.. list-table::
   :widths: 28 28 44
   :header-rows: 1

   * - Method
     - Inherits from
     - Notes
   * - TINTO
     - MappingMethod
     - Feature-to-pixel mapping + coordinates export
   * - IGTD
     - MappingMethod
     - Feature-to-pixel mapping + coordinates export
   * - REFINED
     - MappingMethod
     - Feature-to-pixel mapping + coordinates export
   * - DeepInsight
     - ParamImageMethod
     - Parametric mapping (coords → pixels) + coordinates export
   * - Fotomics
     - ParamImageMethod
     - Parametric mapping (coords → pixels) + coordinates export
   * - BarGraph
     - AbstractImageMethod
     - Standard fit/transform utilities
   * - DistanceMatrix
     - AbstractImageMethod
     - Standard fit/transform utilities
   * - Combination
     - AbstractImageMethod
     - Standard fit/transform utilities
   * - SuperTML
     - AbstractImageMethod
     - Standard fit/transform utilities
   * - FeatureWrap
     - AbstractImageMethod
     - Standard fit/transform utilities
   * - BIE
     - AbstractImageMethod
     - Standard fit/transform utilities

AbstractImageMethod
-------------------

Abstract base class that defines the common training and image-generation
pipeline for all methods.

**Parameters**

- **problem** : str, default='classification'
  The type of problem, defining how the images are grouped.
  Valid values: ['classification', 'unsupervised', 'regression'].
- **verbose** : bool, default=False
  Whether to show execution details in the terminal.
- **transformer** : transformer or None, default=None
  Preprocessing transformation applied to features. Any scikit-learn
  compatible transformer or a custom implementation inheriting
  ``CustomTransformer``.
- **format** : str, default='png'
  Output format using matplotlib images with [0,255] range for pixels or
  ``npy`` format.

**Attributes**

- **problem** : str
  Resolved problem type.
- **verbose** : bool
  Verbosity flag.
- **transformer** : transformer or None
  Preprocessing transformer.
- **format** : str
  Output format used by the method.
- **_fitted** : bool
  Indicates whether ``fit`` has been called.

**Methods**

- **saveHyperparameters(filename='objs.pkl')**
  Saves the configuration to disk as a pickle.
- **loadHyperparameters(filename='objs.pkl')**
  Loads a previously saved configuration.
- **fit(data)**
  Fits the model to tabular data.
- **transform(data, folder)**
  Generates and saves synthetic images.
- **fit_transform(data, folder)**
  Fits the model and generates images in one step.

**Notes**

- Validates input data (numeric only, no missing values).
- Automatically creates output folders and a CSV with image paths.

MappingMethod
-------------

Abstract base class for methods that map each feature to a pixel location.
Inherits from ``AbstractImageMethod``.

**Parameters**

- **problem** : str, default='classification'
- **verbose** : bool, default=False
- **transformer** : transformer or None, default=None
- **zoom** : int, default=1
  Multiplication factor for saving images.
- **format** : str, default='png'
- **cmap** : str or None, default=None
  Matplotlib colormap. Use ``None`` for single-channel images.

**Attributes**

- **zoom** : int
  Zoom level for output images.
- **cmap** : str or None
  Colormap used by matplotlib.
- **_features_mapping** : pandas.DataFrame or None
  Feature-to-pixel mapping table.

**Methods**

- **_get_features_mapping(features=None, columns_names=True)**
  Returns feature positions in the image.

**Notes**

- Exports feature-to-pixel coordinates to ``features_positions.csv``.

ParamImageMethod
----------------

Abstract base class for parametric mapping methods that first extract feature
coordinates and then assign them to pixels. Inherits from ``MappingMethod``.

**Parameters**

- **dim** : int
  Image dimension (square).
- **problem** : str, default='classification'
- **transformer** : transformer or None, default=None
- **verbose** : bool, default=False
- **assignment_method** : str, default='bin'
  Technique to map features to pixels.
- **relocate** : bool, default=False
  Relocate features so each pixel represents a single feature.
- **algorithm_opt** : str, default='linear_sum'
  Optimization algorithm for assignment.
- **group_method** : str, default='avg'
  Strategy to compute pixel values when multiple features map to one pixel.
- **zoom** : int, default=1
- **format** : str, default='png'
- **cmap** : str, default='gray'
- **random_seed** : int, default=1

**Attributes**

- **_image_dim** : int
  Image dimension.
- **_assignment_method** : str
- **_relocate** : bool
- **_algorithm_opt** : str
- **_group_method** : str
- **_random_seed** : int

**Notes**

- Provides default pixel-value aggregation (average) and a relevance-weighted
  alternative when enabled.
