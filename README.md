# MoveMind - Fitness Machine Learning Project

This project analyzes and models sensor data from barbell exercises using machine learning. It provides scripts for data cleaning, feature engineering, model training, and visualization, all tailored for fitness sensor datasets.

## Getting Started

### Prerequisites

- Python 3.9 or higher
- Conda (optional, for environment management)
- Git

### Installation

1. **Clone the repository:**  
   ```bash
   git clone https://github.com/RohanGottipati/MoveMind.git
   cd MoveMind
   ```

2. **Set up the environment:**  
   * With conda (recommended):  
     ```bash
     conda env create -f environment.yml
     conda activate movemind
     ```
   * Or with pip:  
     ```bash
     pip install -r requirements.txt
     ```

3. **Verify installation:**  
   ```bash
   python -c "import sklearn; print('Installation successful!')"
   ```

## Data Preparation

1. **Place your raw data:**  
   Place your raw MetaMotion sensor CSV files in `data/raw/MetaMotion/`.

2. **Process the data:**  
   Run the following scripts to process and clean your data:  
   ```bash
   python src/data/make_dataset.py
   python src/features/remove_outliers.py
   ```

3. **Output locations:**  
   Processed data will be saved in `data/interim/` and `data/processed/`.

## Model Training & Evaluation

1. **Train models:**  
   ```bash
   python src/models/train_model.py
   ```

2. **Customize algorithms:**  
   You can add or modify algorithms in `src/models/LearningAlgorithms.py`.

## Visualization

1. **Generate visualizations:**  
   ```bash
   python src/visualization/visualize.py
   ```

2. **Customize plots:**  
   Adjust plot settings in `src/visualization/plot_settings.py`.

## Notebooks

* Use the `notebooks/` directory for interactive exploration and prototyping with Jupyter.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

## About

 Machine learning system that classifies barbell exercises (bench press, squat, deadlift, etc.) with 89.5% accuracy using wearable sensor data.

