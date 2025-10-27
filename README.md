## Wind Speed Estimation and Conversion Usecase

**Authors:** Mohammad Bakhshandeh – Florida Institute of Technology  
Jean-Paul Pinelli – Florida Institute of Technology  
Steven Cocke – Florida State University  

**Keywords:** hurricane, wind field, interpolation, conversion, exposure correction, Jupyter Notebook, DesignSafe, Florida

## Resources

### Jupyter Notebooks

The following Jupyter notebooks are available to facilitate the analysis of each case.  
You can access and run them directly on **DesignSafe** by clicking the link below:

| **Scope** | **Notebook** |
|------------|---------------|
| Interpolating and converting hurricane wind field data | [Wind_Speed_Estimation.ipynb](https://www.designsafe-ci.org/data/browser/public/designsafe.storage.published/PRJ-5778) <br> [![Open in DesignSafe](https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg)](https://www.designsafe-ci.org/data/browser/public/designsafe.storage.published/PRJ-5778) |


## DesignSafe Resources

The following DesignSafe resources were used in developing this Use Case:

- [Jupyter notebook on DesignSafe JupyterHub](https://www.designsafe-ci.org/rw/workspace/jupyter/)  
- [DesignSafe Publication: Wind Speed Estimation and Conversion (DOI: 10.17603/ds2-kcxr-2683)](https://doi.org/10.17603/ds2-kcxr-2683)  
- [ARA / NIST Hurricane Wind Field Datasets]
 

## Description

The purpose of this Jupyter Notebook is to interpolate and convert gridded hurricane wind field data to property-level locations. The model assigns wind speeds for each site by combining spatial interpolation, exposure conversion, and terrain adjustment. It is suitable for hurricane damage analysis, risk modeling, and catastrophe model calibration.

Key functionalities include:

- **Interpolation:** Derives property-level wind speeds from gridded ARA/NIST hurricane data.  
- **Conversion:** Transforms wind speeds between averaging times (3-sec gusts, 1-min sustained) and exposure categories (marine, open, urban).  
- **Terrain Adjustment:** Applies roughness-based corrections and coastal modifiers using GeoTIFF rasters.  
- **Visualization:** Generates interactive Folium-based maps and static Matplotlib plots for analysis and validation.

## Implementation

### System Requirements

- **Python 3.8+**  
- **Jupyter Notebook environment** (DesignSafe JupyterHub or local)  

Install dependencies before running:
```bash
pip install numpy pandas scipy rasterio folium branca contextily pyproj matplotlib
```

### Steps to Run
1. Download or clone the repository:  
   ```bash
   git clone https://github.com/mbakhshandeh2023/WindSpeed-Estimation-UseCase.git
   ```
2. Open the Jupyter notebook (`Wind_Speed_Estimation.ipynb`).  
3. Update file paths in `config1.txt` as needed.  
4. Run all notebook cells sequentially to perform interpolation, conversion, and mapping.  
5. Outputs (CSV files and HTML maps) will appear in the `Interpolation&ConversionOutput/` directory.

**Run in DesignSafe:**  
[![Open in DesignSafe](https://raw.githubusercontent.com/geoelements/LearnMPM/main/DesignSafe-Badge.svg)](https://www.designsafe-ci.org/rw/workspace/jupyter/)

## Background

This project was developed under the Florida Institute of Technology and Florida State University collaboration to advance wind hazard and vulnerability modeling in Florida. It integrates established wind engineering relationships and geospatial analysis techniques into an accessible, reproducible Jupyter framework.

## Citation and Licensing

If you use this repository, please cite:

> Bakhshandeh, M., Pinelli, J.-P., & Cocke, S. (2025). *Wind Speed Estimation and Conversion.* DesignSafe-CI. DOI: [10.17603/ds2-kcxr-2683](https://doi.org/10.17603/ds2-kcxr-2683)

**License:** BSD 3-Clause License  

**Acknowledgment:**  
This research was supported by the **National Science Foundation (NSF)** under **Award No. 2022469**, through the **NHERI DesignSafe Cyberinfrastructure**. The opinions and conclusions expressed are those of the authors and do not necessarily reflect the views of the NSF.
