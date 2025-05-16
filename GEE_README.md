# Landslide Susceptibility Mapping – GEE Script

This Google Earth Engine (GEE) script prepares training data and generates a baseline landslide susceptibility map for the Kaski District of Nepal. It supports a deep learning project by exporting labeled raster and point datasets used to train a PyTorch-based MLP model.

## 📌 Key Steps in the Script

1. **Filter the Area of Interest**
   - Loads Nepal's district boundaries.
   - Filters to extract only Kaski District.

2. **Load and Clip the Landslide Inventory**
   - Loads a custom landslide catalog dataset.
   - Clips it to Kaski to extract relevant landslide events.

3. **Generate Non-Landslide Samples**
   - Randomly samples 54 points within Kaski.
   - Retains only those located >1 km from any landslide.

4. **Extract Environmental Features**
   - Elevation, slope, and aspect from SRTM DEM.
   - Mean annual precipitation (2000–2023) using CHIRPS daily data.

5. **Feature Stacking and Sampling**
   - Combines all raster features into a single multiband image.
   - Samples raster values at landslide and non-landslide points.
   - Outputs a labeled dataset for model training.

6. **Train and Apply a Random Forest Model**
   - Trains a Random Forest classifier in GEE using the sampled data.
   - Applies the model to generate a probability-based susceptibility map.

7. **Reclassify and Visualize**
   - Converts susceptibility probabilities into 5 risk zones.
   - Adds ROC curve evaluation and computes AUC.

8. **Export / Visual Output**
   - All layers and maps are rendered in the GEE UI.
   - A legend is added for map interpretability.

## 🗂️ Inputs and Assets Used

- `Nepal` – Feature collection of all districts.
- `Landslidecatalogue` – Custom GEE asset of historic landslide events.
- `CHIRPS` – Daily precipitation dataset (UCSB-CHG/CHIRPS/DAILY).
- `SRTM` – Digital elevation data (USGS/SRTMGL1_003).

## 🧪 Outputs

- Pixel-wise landslide susceptibility probability map
- Reclassified 5-level susceptibility map
- Training dataset for use in PyTorch
- ROC curve and AUC for performance evaluation

## 📍 Region of Study

- **District**: Kaski, Nepal
- Chosen for its geological diversity and high landslide risk

## 📜 License

This script is intended for research and academic use only.
