# LandSlide_MLP_Kaski
MLP code for landslide susceptibility map of Kaski, Nepal.
# Landslide Susceptibility Mapping using Deep Learning

This project implements a deep learning-based approach for **Landslide Susceptibility Mapping (LSM)** in the Kaski District of Nepal. It utilizes Google Earth Engine for data extraction, PyTorch for modeling, and rasterio/geopandas for spatial analysis. The model predicts landslide-prone areas based on four key environmental features: elevation, slope, aspect, and precipitation.

## 📁 Repository Structure

├── landslope_mlp_model.ipynb # Google Colab notebook with full implementation
├── GEE_Kaski/
│ ├── kaski_elevation_30m.tif # Input raster: elevation
│ ├── kaski_slope_30m.tif # Input raster: slope
│ ├── kaski_aspect_30m.tif # Input raster: aspect
│ ├── kaski_precipitation_30m.tif # Input raster: precipitation
│ ├── kaski_stack_4band.tif # Stacked 4-band raster (input to DL model)
│ ├── kaski_landslides.geojson # Labeled landslide locations
│ ├── kaski_non_landslides.geojson # Labeled non-landslide locations
│ ├── kaski_susceptibility_map.tif # Output susceptibility probability map
│ └── kaski_susceptibility_refined_highcontrast.png # Final classified visualization


## 🧠 Model Overview

- **Model**: Multilayer Perceptron (MLP)
- **Framework**: PyTorch
- **Input Features**: Elevation, Slope, Aspect, Precipitation
- **Target**: Binary label (landslide = 1, non-landslide = 0)
- **Output**: Landslide susceptibility probabilities and 5-class risk zone map

### 🔍 Architecture
- Input Layer: 4 neurons (1 per feature)
- Hidden Layers: 64 → 32 neurons with ReLU, BatchNorm, Dropout
- Output Layer: 2 neurons (Softmax for binary classification)
- Loss: CrossEntropyLoss
- Optimizer: Adam
- Regularization: Dropout (0.3), Early Stopping

## 📊 Results

- **Test Accuracy**: ~66.7%
- **Confusion Matrix** and **Classification Report** included
- Final map classifies areas into:
  - Very Low
  - Low
  - Medium
  - High
  - Very High susceptibility

![Final Map](GEE_Kaski/kaski_susceptibility_refined_highcontrast.png)

## 🚀 Running the Project

1. Upload the `.ipynb` file to **Google Colab**
2. Mount Google Drive containing the `GEE_Kaski` folder
3. Run all cells to:
   - Preprocess raster data
   - Train the model
   - Evaluate performance
   - Generate and save output maps

## 📦 Requirements

Install the following Python packages (Google Colab pre-installs most):
```bash
!pip install rasterio geopandas scikit-learn imbalanced-learn matplotlib scipy

📍 Case Study Region
Location: Kaski District, Nepal

Reason: Moderate terrain diversity and manageable data volume for prototyping

📚 References
Data: NASA GLC Landslide Catalog

Code inspired by various landslide mapping research papers listed in the final report.

See full citations in the Project Report.pdf

👥 Authors
Isaac Kosgey (ECE, ISU)

Md Shazzadul Islam (ECE, ISU)

Nabin Budhathoki (Civil Engg., ISU)

Md Samiullah Chowdhury (Civil Engg., ISU)

📝 License
This project is for educational and research purposes only. Please cite the repository or final report if used in derivative work.


