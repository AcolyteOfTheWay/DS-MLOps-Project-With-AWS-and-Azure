# DS-MLOps-Project-With-AWS-and-Azure

**Source:** repository uploaded from `https://github.com/AcolyteOfTheWay/DS-MLOps-Project-With-AWS-and-Azure`

---

## Project description
This repository implements a student exam performance prediction project. It contains data, model artifacts, Jupyter notebooks (EDA and model training), a Flask web application for prediction, and MLOps-related configuration for deployment to **Azure App Service** and **AWS Elastic Beanstalk**.

> Note: Several Python source files in `src/` contain placeholder sections represented by `...`. The repository includes pre-trained artifacts (`artifacts/model.pkl`, `artifacts/preprocessor.pkl`) and notebooks which provide the training and EDA context.

---

## Python / Packaging
- Python version: **3.12** (file: `.python-version` and `pyproject.toml`).
- Packaging metadata: `pyproject.toml`, `setup.py` (package name in setup: `mlopsproject`, author `Jordan`).

---

## Requirements (from `requirements.txt`)
- pandas
- numpy
- seaborn
- matplotlib
- scikit-learn
- catboost
- xgboost
- Flask

---

## Tools, frameworks and infra referenced in the repo
- Python 3.12
- Flask (web application)
- scikit-learn (preprocessing, model utilities)
- CatBoost (model training artifacts present; `catboost` in requirements and `catboost_info/` folders)
- XGBoost (`xgboost` in requirements)
- pandas, numpy, seaborn, matplotlib
- GitHub Actions (workflow present in `.github/workflows/main_studentssperformance3.yml`)
  - Uses `azure/webapps-deploy@v2` to deploy to an Azure Web App (`studentssperformance3`)
- AWS Elastic Beanstalk configuration (`.ebextensions/python.config`) — WSGI path set to `application:application`
- setuptools (`setup.py`) / project packaging
- Jupyter Notebooks (two notebooks under `notebook/`)

---

## Important files and folders (what's included)
- `app.py` — Flask application (defines routes and uses `src.pipeline.predict_pipeline.PredictPipeline`).
- `main.py` — simple entrypoint printing a greeting.
- `requirements.txt` — Python dependencies.
- `pyproject.toml` / `setup.py` — packaging metadata.
- `.python-version` — contains `3.12`.
- `.ebextensions/python.config` — Elastic Beanstalk WSGI configuration.
- `.github/workflows/main_studentssperformance3.yml` — GitHub Actions workflow to build & deploy to Azure Web App.
- `templates/` — HTML templates:
  - `index.html`
  - `home.html` (form for prediction; field names correspond to features used by the pipeline)
- `artifacts/` — model and data artifacts:
  - `model.pkl` (pre-trained model artifact)
  - `preprocessor.pkl` (preprocessing pipeline artifact)
  - `train.csv`, `test.csv`, `data.csv` (dataset extracts)
- `catboost_info/` — CatBoost training metadata (JSON, logs, TF events).
- `notebook/` — Jupyter notebooks:
  - `1 . EDA STUDENT PERFORMANCE .ipynb`
  - `2. MODEL TRAINING.ipynb`
  - notebook `data/stud.csv`
- `src/` — Python package source:
  - `src/components/`
    - `data_ingestion.py` — data ingestion component (contains placeholders `...`)
    - `data_transformation.py` — data transformation (contains placeholders `...`)
    - `model_trainer.py` — model training component (contains placeholders `...`)
  - `src/pipeline/`
    - `train_pipeline.py` — orchestrates training (contains placeholders `...`)
    - `predict_pipeline.py` — prediction pipeline; includes `PredictPipeline` and `CustomData` classes (file contains `...` in places). Uses `artifacts/model.pkl` and `artifacts/preprocessor.pkl`.
  - `src/utils.py` — utility functions (includes `save_object`, `load_object` used by pipelines).
  - `src/logger.py` — logging configuration (writes logs to `logs/` with timestamped filenames).
  - `src/exception.py` — `CustomException` wrapper class.
  - `src/__init__.py`
- `.gitignore` — standard ignore rules.
- `README.md` — (currently empty; this file is the generated README).
  
---

## How to run (based strictly on repository contents)
1. Ensure Python 3.12 is used (file `.python-version` indicates `3.12`).
2. Install dependencies from `requirements.txt`:
   ```bash
   pip install -r requirements.txt
Run the Flask app:

bash
Copy code
python app.py
The application in app.py calls app.run(host="0.0.0.0") when __main__. The Elastic Beanstalk config references the WSGI application object as application in the repository root.

The repository contains pre-trained artifacts/model.pkl and artifacts/preprocessor.pkl so the prediction endpoint can use them (unless the code placeholders ... prevent execution).

CI / CD and deployment details (as present in repo)
GitHub Actions workflow (.github/workflows/main_studentssperformance3.yml) is configured to build and deploy to Azure Web App studentssperformance3 using azure/webapps-deploy@v2 and an Azure publish profile secret.

AWS Elastic Beanstalk configuration (.ebextensions/python.config) sets WSGIPath: application:application, which matches the Flask application variable defined in app.py. This indicates an intended Elastic Beanstalk deployment option is present.

Notes / Current repository state (literal, as present)
Several Python files in src/ contain ... placeholder sections. These files may be incomplete and could cause runtime errors if executed as-is.

README.md in the original repository root was empty; this file documents the repository contents exactly as they appear in the uploaded archive.

setup.py uses get_requirements('requirements.txt') and defines package metadata: name='mlopsproject', version='0.0.1', author Jordan.
