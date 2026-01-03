# Satellite Imagery Based Property Valuation

This project predicts property prices by combining traditional housing data with satellite imagery analysis.

## Project Overview

We start with **Exploratory Data Analysis (EDA)** to examine price distributions and understand how features like location, area, and room count affect property values. From this foundation, we train and evaluate several **tabular models**, including **Linear Regression (LR)**, **Polynomial Regression**, and **XGBoost (XGB)**.

To capture visual information from property surroundings, we train a **CNN-based image model using ResNet18**. We chose this lightweight architecture to work within computational constraints while still extracting meaningful spatial features from satellite images.

For better interpretability, we apply **Grad-CAM** to visualize which parts of satellite images most influence the CNN's predictions.

The final step brings everything together in a **fusion model** that combines predictions from both the **tabular XGBoost model** and the **image-based CNN model**. We stack their outputs and feed them to a meta-learner, achieving better performance than either model alone.

This multimodal approach shows how structured data and visual context can work together to create more accurate and interpretable property valuations.

## Project Files

- **`23322001_report.pdf`** - Comprehensive project report with methodology and results
- **`23322001_final.csv`** - Final test predictions output
- **`preprocessing+model-training.ipynb`** - Main notebook containing data preprocessing, model training, and evaluation
- **`data_fetcher.ipynb`** - Image downloader using Google Maps Static API

## Dataset

This project uses the **Data-CDC** dataset from Kaggle. Since the dataset is approximately 3.1 GB, it cannot be hosted directly on GitHub and must be downloaded separately.

**Kaggle Dataset URL:**  
https://www.kaggle.com/datasets/tasteing/data-cdc

## Downloading the Dataset

You'll need the Kaggle CLI installed and configured with your API token.

### Install Kaggle CLI

```bash
pip install kaggle
```

### Configure API Token

Place your `kaggle.json` file in the appropriate directory and set permissions:

```bash
chmod 600 ~/.kaggle/kaggle.json
```

### Download and Extract Data

```bash
mkdir -p data
kaggle datasets download -d tasteing/data-cdc -p data
unzip data/data-cdc.zip -d data
```

### Expected Data Structure

```
data/
  ├── images_train/
  ├── images_test/
  ├── train.csv
  └── test.csv
```

## Getting Started

1. Download the dataset following the instructions above
2. Open `data_fetcher.ipynb` if you need to fetch additional satellite images
3. Run `preprocessing+model-training.ipynb` to train models and generate predictions
4. Review `23322001_report.pdf` for detailed methodology and analysis
5. Check `23322001_final.csv` for the final prediction results
