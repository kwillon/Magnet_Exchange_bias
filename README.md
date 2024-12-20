<div align='middle'><img src='Data\Fig_1_TOC.jpg' style='width: 100%; min-width: 300px;'/></div>

# Prediction of exchange bias for magnetic heterostructures nanoparticles with machine learning

**Magnetic heterostructures nanoparticles and exchange bias** are critical for enhancing the stability and control of magnetization in spintronic devices, magnetic storage systems, and sensors. Exchange bias (EB) plays a crucial role in these technologies, helping to stabilize magnetic orientations.

Currently, EB is employed to improve the regeneration of human tissues, MRAM memory circuits, and spin electronics through the empirical selection of a new hard magnetic layer. Advanced applications also utilize exchange bias to increase the stability of small magnetic particles, which would otherwise exhibit superparamagnetic behavior without this correction.

In our work, we compare different approaches to predicting exchange bias and interpreting the influence of other nanoparticle parameters on exchange bias. This analysis allows us to assess how various factors, such as particle size, shape, composition, and magnetic interactions, impact the overall behavior of exchange bias, providing deeper insights into optimizing these materials for advanced applications.

# Project Implementation

<div align='middle'><img src='Data\Fig_2_Pipeline_SVG-01.svg' style='width: 100%; min-width: 300px;'/></div>

### Data Collection

We collected data from open scientific sources for 1299 samples with various characteristics, including core material, shell material, space group of the core and shell, magnetic field, blocking temperature, Neel temperature, Curie temperature, nanoparticle width, length, and height in nanometers, nanoparticle shape, experimental temperature, saturation magnetization, remanent magnetization, coercivity, exchange bias, exchange bias direction, vertical shift, vertical shift direction, and additional magnetic field. All the necessary datasets are stored in the same folder with notebook or in the `Data` folder.

### Data preprocessing and processing

First, we removed features that could not be imputed, and then we filled in the missing values using the KNN method. Second, we enriched our features by creating custom functions and utilizing the Pymatgen library. We also generated new features, including sphericity, the ratio of the largest to smallest nanoparticle size, lattice parameters of the core and shell materials, the number of magnetic ions in the nanoparticles, the ratio of the difference between the blocking temperature and Néel temperature, the electronegativity of the core and shell, valence electron concentration for the core and shell, and the work function for the core and shell.  When using files from the `preprocessing and processing` folder, it's important to follow the correct order: first, run `preprocessing and processing\preprocessing_deal_bias.ipynb`, and only then proceed with `preprocessing and processing\add_new_parameters\add_new_parameter.ipynb`. The second notebook requires Pymatgen, so make sure to obtain an API key for it.

### Data visualisation

We created visualizations using pie charts to represent all materials, as well as for the cores and shells separately. Additionally, we generated a correlation matrix and violin plots for all the features we obtained. All visualisation is presented in the folder `visualisation`. The model visualizations and SHAP visualizations are stored in the respective folders or files associated with their training, specifically in `models\classic_ML` and `models\KAN_and_comparison`.

### Models

We trained both classical machine learning models and a new neural network based on Kolmogorov-Arnold networks (*KAN*). The *XGB* model produced the best results among the machine learning methods, which is why it was compared to KAN in our study. Interestingly, XGB and KAN highlighted different features as important for predicting exchange bias. Additionally, KAN demonstrated a less stable and more complex structure, making it harder to train. This is an intriguing and significant finding in our research.

## Magnet_Exchange_bias

Magnet_Exchange_Bias is a scientific project for 2023-2024 that aims to predict the exchange bias shift in heterostructural magnetic nanoparticles and compare classical ML models with the new Kolmogorov-Arnold Networks model.