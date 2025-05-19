# CNC_Cost_Estimation

The goal of this assignment is to estimate CNC machining costs using data science methodologies.
## Method 1: Using Dataset (CSV)

###  Data Summary
- Dataset: `FeatureAndMetadata_Milling.csv`
- Features: Sensor statistics, material type, tool geometry, hardness, machining parameters.
- Target: `CycleToFailure` (proxy for cost/time)

### Steps Taken
1. Loaded data and handled missing values.
2. Feature engineered: average current across axes, encoded material/tool type.
3. Used **Random Forest** and **Neural Network** models.
4. Evaluated performance using MAE and RMSE.

### Model Performance
- MAE ≈ 12.72
- RMSE ≈ 16.76

### Insights
- Mean spindle current and tool type were key features.
- Normalization helped stabilize neural network training.


## 🌐 Method 2: Web-Scraped Dataset (Xometry)

### Data Summary
- Scraped from: [Xometry Milling Cost Estimator](https://www.xometry.com/resources/machining/milling-cost-estimator/)
- Extracted: Material, Dimensions, Estimated Time, Estimated Cost
- Engineered: Volume, Cost per Volume, Material Encoded

### Steps Taken
1. Scraped cost tables using BeautifulSoup.
2. Parsed dimension strings into numeric length, width, height.
3. Calculated volume and encoded material type.
4. Trained a **Neural Network** to predict cost.

### Model Performance
- MAE: 12.54
- RMSE: 12.54

### Visualizations
- Cost distribution histogram
- Boxplot of cost vs material
- Predicted vs Actual scatter plot


## Final Comparison

| Metric        | Method 1 (CSV) | Method 2 (Scraped) |
|---------------|----------------|--------------------|
| MAE           | 12.72          | 12.54              |
| RMSE          | 16.76          | 12.54              |
| Interpretability | High (RandomForest) | Medium (NN)       |
| Real-World Context | Moderate         | High               |


## Improvements & Future Work

- Add more vendors (e.g., Fictiv, Alibaba) to improve variety.
- Use CAD complexity scores for precision modeling.
- Implement model deployment via web UI for interactive predictions.
