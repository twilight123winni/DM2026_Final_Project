# DM2026_Final_Project 2026 Spring

## Overview

This repository contains the code for the **Data Mining Final Project (Spring 2026)**.

The objective of this project is to predict **weekly drought severity scores (0–5)** for 2,248 regions over the next **5 weeks**, using only historical meteorological observations.

---

## Project Structure

```text
.
├── Data_Mining_Final-Project_Notebook.ipynb
├── requirements.txt
└── README.md
```


## Dataset

The dataset is not included in this repository.

The original notebook was developed using a Kaggle dataset path:

```python
train_data_path = '/kaggle/input/datasets/.../train.csv'
test_data_path = '/kaggle/input/datasets/.../test.csv'
```

To run this project, you need to:

1. Obtain the dataset separately.
2. Download the training and testing files.
3. Replace all dataset paths inside the notebook with your local paths.

Example:

```python
train_raw = pd.read_csv("./data/train.csv")
test_raw = pd.read_csv("./data/test.csv")
```

Suggested directory structure:

```text
project/
│
├── data/
│   ├── train.csv
│   └── test.csv
│
├── Data_Mining_Final-Project_Notebook.ipynb
├── requirements.txt
└── README.md
```

---

## Methodology

### 1. Data Preprocessing

Parse date and sort by ID and date

### 2. Feature Engineering

The notebook generates a variety of temporal and climate-related features, including:

#### Rolling Window Features

Historical statistics computed using 1,2,4,7,12 weeks look-back windows:


#### Climate Baseline Features

Climate-normalized variables are constructed by comparing current observations against historical averages.

#### Evaporation Stress Indicator

A custom feature is created:

```text
evap_stress = tmp_max × (100 − humidity)
```

### 3. Multi-Step Forecasting

A multi-output regression framework is used to predict all future weeks simultaneously.

### 4. Model

Our best performance achieves a **Kaggle public-leaderboard MAE of 0.7896**, beating the Baseline 3 (0.8056).

---

## Installation

Create a Python environment and install dependencies:

```bash
pip install -r requirements.txt
```

---

## How to Run

Open the notebook:

```bash
jupyter notebook Data_Mining_Final-Project_Notebook.ipynb
```

Run all cells sequentially:

```text
Kernel
 └── Restart & Run All
```

---

## Final Notes

* The dataset is not distributed with this repository.
* Users must provide their own copy of the competition dataset.
* Dataset paths inside the notebook may need to be modified before execution.


