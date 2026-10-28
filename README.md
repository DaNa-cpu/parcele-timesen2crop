# Dataset Card — TimeSen2Crop
**Project A4: Crop Phenology and Stability in Austria**

### 1. Data source
TimeSen2Crop is a public dataset of Sentinel-2 satellite image time series developed for crop-type classification in Austria. It was created using an Austrian crop-type map based on farmers’ declarations.

**Source:** https://zenodo.org/records/4715631  
**Reference:** Weikmann, G., Paris, C., & Bruzzone, L. (2021). *TimeSen2Crop: A Million Labeled Samples Dataset of Sentinel 2 Image Time Series for Crop-Type Classification.* IEEE JSTARS, 14, 4699–4708. https://doi.org/10.1109/JSTARS.2021.3073965

### 2. Temporal coverage
The main dataset covers the 2017–2018 agricultural year, from **September 2017 to August 2018**. Additional time series for one tile cover September 2018 to August 2019.

### 3. Spatial resolution
The dataset provides Sentinel-2 spectral observations at **10 m spatial resolution**. Samples represent individual pixels within Sentinel-2 tiles covering Austria.

### 4. Temporal resolution
Acquisition dates are **irregular**, depending on satellite acquisitions, tile coverage, and image-quality filtering. The original dataset provides a date list for each tile. Therefore, the effective observation frequency and temporal gaps must be assessed from the corresponding `dates.csv` file.

### 5. Units and variables
Each sample contains time-series observations for nine spectral bands: B2, B3, B4, B5, B6, B7, B8A, B11, and B12.

The data are atmospherically corrected spectral measurements. The numerical scale and units must be verified from the dataset documentation and CSV values before analysis. A quality-condition variable identifies clear observations (0), clouds (1), shadows (2), and snow (3).

### 6. Number of samples
The original dataset contains **more than one million pixel-level time series** associated with 16 crop types.

The exact number of CSV samples in the downloaded project subset will be calculated during data inspection. File counts must not be interpreted as parcel counts because each sample represents a pixel, not necessarily a complete agricultural parcel.

### 7. Missing observations and data gaps
Time series may contain observations affected by clouds, shadows, or snow, as well as gaps between acquisition dates. These conditions will be quantified during preprocessing. Quality-affected observations will be flagged or excluded according to a documented rule. No temporal interpolation will be applied without evaluating its effect on phenology estimates.

### 8. Train/test split
The project will use a preliminary **70% training, 15% validation, and 15% test split**. The split will be reproducible using a fixed random seed.

To reduce spatial data leakage, samples should be separated by geographic group where the available metadata permit it. The split unit and the final sample counts will be reported after inspecting the dataset structure. These percentages describe the planned project split, not a claim about the original dataset’s official partition.

### 9. License
The original TimeSen2Crop dataset is distributed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. Reuse and redistribution should include appropriate attribution and comply with the license terms.

License information: https://creativecommons.org/licenses/by/4.0/

### 10. Limitations and intended use
TimeSen2Crop was designed primarily for pixel-level crop-type classification. It does not necessarily provide parcel polygons, unique parcel identifiers, or ready-made start-of-season (SOS) and end-of-season (EOS) labels.

For this project, SOS and EOS will need to be estimated from suitable vegetation-index or spectral time series using a documented phenology method. **Parcel-level stability cannot be established from pixel samples alone** without reliable parcel boundaries or identifiers and a valid method for associating pixels with parcels.

The dataset can support exploratory analysis of seasonal crop signals, but a treatment calendar also requires agronomic validation and additional context, such as crop-specific management requirements and weather conditions.
