# Current Transformers FDD and RUL Datasets

## Overview
This dataset contains time-series data on dissolved gas concentrations in power transformer oil. It is designed to aid in solving two main problems:
1. **Fault Detection and Diagnosis (FDD)**: Classifying the operational state of power transformers into one of several modes based on gas concentration data.
2. **Remaining Useful Life (RUL) Prediction**: Predicting the time remaining until transformer failure.

This dataset is valuable for researchers and practitioners working on transformer health monitoring, fault detection, and predictive maintenance using machine learning techniques.

## Purpose
Power transformers (PTs) are essential components in the electrical grid, and their proper functioning is crucial to power system reliability. By using machine learning models trained on this dataset, researchers can develop systems for fault detection, diagnostics, and RUL prediction, which help extend the life of transformers and prevent failures.

## Dataset Description
The dataset consists of time-series data on the concentration of dissolved gases in the oil of power transformers. The gases analyzed are:
- **Hydrogen (H₂)**
- **Carbon Monoxide (CO)**
- **Ethylene (C₂H₄)**
- **Acetylene (C₂H₂)**

The dataset includes records of gas concentrations collected at 12-hour intervals over time. The goal is to predict the condition of the transformer (FDD) or its remaining useful life (RUL) based on these concentrations.

### Data Files:
- **Training and Test Data**: The dataset is split into training (2100 datasets) and test (900 datasets) sets.
  - `data_train/`: Contains the training datasets.
  - `data_test/`: Contains the test datasets.
- **Labels for Fault Detection and Diagnosis (FDD)**:
  - `labels_fdd_train.csv`: Labels for the training set indicating the operational mode.
  - `labels_fdd_test.csv`: Labels for the test set.
- **Labels for Remaining Useful Life (RUL)**:
  - `labels_rul_train.csv`: Labels for the RUL prediction training set.
  - `labels_rul_test.csv`: Labels for the RUL prediction test set.

### Categories of Labels:
The labels for FDD consist of four operational modes:
1. **Normal Mode** (2436 datasets)
2. **Partial Discharge** (127 datasets)
3. **Low-Energy Discharge** (162 datasets)
4. **Low-Temperature Overheating** (275 datasets)

For RUL prediction, each dataset file includes a corresponding label indicating the remaining time until transformer failure.

## Problem Statements

### Fault Detection and Diagnosis (FDD)
The FDD task involves classifying the operational state of the transformer based on the gas concentration data. This is a **multiclass classification** problem, where the goal is to predict one of the four possible operating modes (Normal, Partial Discharge, Low-Energy Discharge, Low-Temperature Overheating).

Additionally, the FDD problem can be approached as a **binary classification** problem to detect whether a transformer is in a "normal" or "anomalous" state.

### Remaining Useful Life (RUL) Prediction
RUL prediction is critical for the maintenance and repair of transformers. The task is to develop a model that can predict how many time points (12-hour intervals) remain before the transformer fails based on the concentration of dissolved gases.

## Data Format

The data is presented in CSV files with the following format:

1. **Transformer Data**: Each dataset represents one transformer and consists of a time series of gas concentration values for the gases: H₂, CO, C₂H₄, and C₂H₂.
   - The rows represent time points, and the columns represent the concentration of each gas at each time point.
   - Time is recorded at 12-hour intervals.
2. **Labels for FDD**: These files contain labels for the operational state of the transformer, with one of the following categories:
   - `1.0 - 1.3`: Normal mode
   - `1.9 - 2.2`: Partial Discharge
   - `2.8 - 3.1`: Low-Energy Discharge
   - `3.7 - 4.0`: Low-Temperature Overheating
3. **Labels for RUL**: These files contain a single value that represents the remaining time until the transformer fails (in 12-hour intervals).

### Example:
- **File Format**:
    ```
    time, H2, CO, C2H4, C2H2
    0, 10.5, 5.2, 3.1, 1.4
    12, 10.7, 5.3, 3.0, 1.5
    24, 10.9, 5.4, 3.2, 1.6
    ...
    ```
    Each row represents one observation (gas concentration values at a specific time point).

## Installation and Usage

To start using the dataset, simply download the CSV files from this repository and load them into your machine learning pipeline. Below is a basic Python example of how to load the data using `pandas`:

```python
import pandas as pd

# Load the training data
train_data = pd.read_csv('path_to_data_train/your_dataset.csv')

# Load the FDD labels
fdd_labels = pd.read_csv('labels_fdd_train.csv')

# Load the RUL labels
rul_labels = pd.read_csv('labels_rul_train.csv')



### Key Sections Explained:
- **Overview**: Provides a brief introduction to what the dataset is about.
- **Dataset Description**: Explains the structure of the data, the gases involved, and the time intervals.
- **Problem Statements**: Describes the two primary problems that the dataset addresses (FDD and RUL).
- **Data Format**: Clarifies the structure of the data files, including a sample.
- **Installation and Usage**: Provides basic instructions on how to use the dataset in Python.
- **Research and Applications**: Shows how others have used the dataset in real research.
- **License**: Specifies the license under which the data is shared.
- **Contact**: A place for people to reach out for support or questions about the dataset.

This README should be informative and easy to follow for any user on GitHub. It will help ensure that anyone accessing the repository understands the dataset, how to use it, and how to contribute to its improvement.
