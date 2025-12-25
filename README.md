# Satellite Imagery Based Property Valuation


This project focuses on **property price prediction using both tabular housing data and satellite imagery**.

We begin with **Exploratory Data Analysis (EDA)** to understand the distribution of prices and the impact of key features such as location, area, and number of rooms. Based on this analysis, multiple **tabular models** were trained and evaluated, including **Linear Regression (LR)**, **Polynomial Regression**, and **XGBoost (XGB)**.

To incorporate visual information, we trained a **CNN-based image model using ResNet18**. A lightweight architecture was chosen due to limited computational resources, while still capturing meaningful spatial features from satellite images.

For model interpretability, **Grad-CAM** was applied to visualize which regions of the satellite images influenced the CNN’s predictions.

Finally, we developed a **fusion model** that combines predictions from the **tabular XGBoost model** and the **image-based CNN model**. The outputs of both models are stacked and passed to a meta-learner, resulting in improved performance compared to using tabular or image data alone.

This multimodal approach demonstrates how combining structured data with visual context can lead to more accurate and interpretable property valuation models.


##  Dataset

This project uses the **Data-CDC** dataset from Kaggle.  
Because the dataset (~3.1 GB) is too large for direct GitHub hosting, it must be downloaded separately.

**Kaggle Dataset URL:**  
https://www.kaggle.com/datasets/tasteing/data-cdc



## To Download the Data

You need the Kaggle CLI installed and configured with your API token.

### Install Kaggle CLI

```
pip install kaggle

chmod 600 ~/.kaggle/kaggle.json
mkdir -p data
kaggle datasets download -d tasteing/data-cdc -p data
unzip data/data-cdc.zip -d data

```
Structure :
```
data/
  ├── images_train
  ├── images_test
  ├── train.csv
  └── test.csv
```

