## Wind Speed Estimation and Conversion UseCase

**Authors:** Mohammad Bakhshandeh – Florida Institute of Technology  
Jean-Paul Pinelli – Florida Institute of Technology  
Steven Cocke – Florida State University  

**Key Words:** hurricane wind field, interpolation, exposure correction, Jupyter Notebook, DesignSafe, Florida

---

## Overview

The *Wind Speed Estimation and Conversion* Jupyter Notebook provides a flexible and reproducible framework for assigning wind speeds to property locations in Florida that were damaged during hurricanes. The notebook accepts wind field input data in any grid format and for different exposure types (marine, open terrain, or urban) and averaging times (3-second gusts, 1-minute sustained, or 10-minute averages). It can also convert wind speeds between heights using standard wind engineering relationships.

The tool performs three major functions:

1. **Linear interpolation** of gridded wind data to property coordinates using spatial interpolation methods.  
2. **Conversion** of wind speeds between exposure types, time averages, and reference heights using empirical and analytical relationships.  
3. **Terrain adjustment**, applying real-world corrections based on surface roughness and coastal proximity, derived from GeoTIFF data layers.

This notebook supports both research and operational needs for catastrophe and vulnerability modeling, integrating datasets from sources such as ARA/NIST and DesignSafe Reconnaissance Portal.

---

## Workflow

The workflow is structured as follows:

1. **Data Preparation:** Import gridded hurricane wind field data, property location files (latitude and longitude), and terrain rasters (`rough_2022.tif`, `distance_2022.tif`).  
2. **Interpolation:** Apply deterministic linear interpolation (`scipy.interpolate.griddata`) to estimate wind speeds at each property location.  
3. **Conversion:** Adjust interpolated values for time averaging (e.g., 1-min to 3-sec gust), exposure type (marine to urban), and height differences using gust factor binaries (`gfac_3sec.dat`, `gfac2_3sec.dat`, `gfacm.dat`, `gfaco.dat`).  
4. **Terrain Adjustment:** Apply logarithmic scaling to account for local surface roughness and coastal effects (e.g., 15% reduction in urban areas, 10–15% increase near coastlines).  
5. **Output and Visualization:** Export adjusted results (`interpolated.csv`, `wind_speeds_conversion.csv`) and generate static and interactive maps (Matplotlib and Folium).

---

## Resources

The following resources are available to reproduce and explore this use case:

- **Jupyter Notebook:** `Wind_Speed_Estimation.ipynb`  
- **Configuration File:** `config1.txt` – defines input/output paths, exposure types, and time intervals  
- **Input Data:** hurricane wind fields (ARA/NIST datasets or user-provided CSVs)  
- **Terrain Data:** roughness and distance rasters provided by Dr. Steven Cocke (Florida State University)  
- **Outputs:** CSV tables of interpolated and terrain-adjusted wind speeds, and interactive maps  

**DesignSafe Publication:** [10.17603/ds2-kcxr-2683](https://doi.org/10.17603/ds2-kcxr-2683)  

---

## Implementation

### System Requirements
- Python 3.8 or higher  
- Jupyter Notebook environment  
- Required libraries:
  ```bash
  pip install numpy pandas scipy rasterio folium branca contextily pyproj matplotlib
  ```

### How to Run
1. Clone the repository or download the notebook files.  
2. Update file paths in `config1.txt` as needed.  
3. Run all notebook cells in order.  
4. Review generated outputs and visualizations.

---

## Using Jupyter Notebooks

You can run the notebook locally or through DesignSafe’s JupyterHub service.

**Accessing on DesignSafe:**
1. Log in to [DesignSafe-CI.org](https://www.designsafe-ci.org).  
2. Navigate to **JupyterHub** under *Workspace → Tools → Jupyter*.  
3. Locate the project under *Published Data → PRJ-5778 – Wind Speed Estimation and Conversion*.  
4. Open `Wind_Speed_Estimation.ipynb` and execute the cells to reproduce the analysis.

**Running Locally:**
```bash
git clone https://github.com/<your-username>/WindSpeed-Estimation-UseCase.git
jupyter notebook Wind_Speed_Estimation.ipynb
```

---

## Background

This Jupyter Notebook was developed as part of ongoing research at the Florida Institute of Technology and Florida State University to improve hurricane wind field estimation and terrain adjustment modeling. The methodology integrates validated empirical relationships from wind engineering and boundary-layer meteorology, using open and reproducible computational tools.

---

## Citation and Licensing

If you use this repository, please cite:

> Bakhshandeh, M., Pinelli, J.-P., & Cocke, S. (2025). *Wind Speed Estimation and Conversion.* DesignSafe-CI. DOI: [10.17603/ds2-kcxr-2683](https://doi.org/10.17603/ds2-kcxr-2683)

**License:** BSD 3-Clause License  

**Acknowledgment:**  
This research was supported by the **National Science Foundation (NSF)** through **Award No. 2022469**, within the **NHERI DesignSafe Cyberinfrastructure** program. The findings and opinions are those of the authors and do not necessarily represent the views of the NSF.
