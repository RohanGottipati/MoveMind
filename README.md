# MoveMind

Machine learning project for classifying barbell exercises (bench press, squat, deadlift, etc.) from wearable MetaMotion sensor data.

> **Status:** early scaffold. The package structure, function signatures and CLI entry points are in place, but the data loading, cleaning, outlier removal, training and plotting functions are still placeholders (they currently return `None`). Running the scripts only prints a status message.

## Project structure

```
MoveMind/
├── environment.yml              # Conda environment (Python 3.9, installs requirements.txt via pip)
├── requirements.txt             # Pinned pip dependency ranges
└── src/                         # Importable package (`import src`)
    ├── data/
    │   └── make_dataset.py      # load_raw_data(), clean_data() – raw sensor CSVs → cleaned DataFrame
    ├── features/
    │   └── remove_outliers.py   # remove_outliers(df, method='iqr' | 'zscore')
    ├── models/
    │   ├── LearningAlgorithms.py  # ExerciseClassifier (algorithm='random_forest' | 'svm'; fit/predict)
    │   └── train_model.py         # train_model(X, y, test_size=0.2, random_state=42)
    └── visualization/
        ├── plot_settings.py     # Shared plot style, figure size, DPI, exercise colour palette, font sizes
        └── visualize.py         # plot_sensor_data(), plot_confusion_matrix()
```

Each subpackage re-exports its public functions, e.g. `from src.models import ExerciseClassifier, train_model`.

## Tech stack

Python 3.9 · pandas · NumPy · scikit-learn · matplotlib · seaborn · Jupyter (see `requirements.txt` for version ranges).

## Prerequisites

- Python 3.9 (the version pinned in `environment.yml`; the `pandas<2.0` pin limits you to Python ≤ 3.11)
- Conda (optional, for environment management)
- Git

## Setup

```bash
git clone https://github.com/RohanGottipati/MoveMind.git
cd MoveMind
```

With conda (recommended):

```bash
conda env create -f environment.yml
conda activate movemind
```

Or with pip (ideally inside a virtual environment):

```bash
pip install -r requirements.txt
```

Verify the installation:

```bash
python -c "import sklearn; print('Installation successful!')"
```

## Running the pipeline

Run the modules from the repository root with `python -m` (the package uses relative imports, so `python src/visualization/visualize.py` fails with an `ImportError`):

```bash
python -m src.data.make_dataset            # load and clean raw sensor data
python -m src.features.remove_outliers     # remove outliers
python -m src.models.train_model           # train and evaluate models
python -m src.visualization.visualize      # generate plots
```

Raw MetaMotion CSV exports are intended to go in `data/raw/MetaMotion/`, with intermediate and processed outputs in `data/interim/` and `data/processed/`. These directories are git-ignored (as are `*.csv`, `*.pkl`, `*.h5`, `*.joblib` and `*.ipynb` files), so create them locally. No script reads or writes them yet.

## Customising

- Algorithms: `src/models/LearningAlgorithms.py`
- Plot style, colours and sizes: `src/visualization/plot_settings.py`

## Contributing

Contributions are welcome. Fork the repository and open a pull request.
