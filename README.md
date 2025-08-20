# Titanic EDA (Exploratory Data Analysis)

Analyze the classic **Titanic** passenger dataset to explore survival patterns by sex, age, class, family size, fare, and embarkation. This project walks through a clean, reproducible EDA workflow with clear visuals and well‑commented notebooks/scripts—perfect for learning, showcasing on a resume, or serving as a starter template for deeper modeling.

---

## 🔍 Objectives
- Load and audit the dataset (schema, types, missingness, duplicates).
- Clean and engineer helpful features (e.g., `Title`, `FamilySize`, `IsAlone`, `Deck`).
- Univariate and bivariate analysis to understand survival drivers.
- Visualize insights with Matplotlib/Seaborn (and optional Plotly).
- Produce a short “findings” report and recommendations for modeling.

---

## 📦 Project Structure
```
Titanic_EDA/
├─ data/
│  ├─ raw/              # place original CSVs here (e.g., train.csv, test.csv)
│  ├─ interim/          # optional: intermediate cleaned files
│  └─ processed/        # optional: final cleaned files used for charts
├─ notebooks/
│  └─ 01_titanic_eda.ipynb
├─ src/
│  ├─ __init__.py
│  ├─ data.py           # loading, auditing, cleaning utilities
│  ├─ features.py       # feature engineering helpers
│  └─ viz.py            # plotting utilities
├─ reports/
│  ├─ figures/          # exported charts (PNG)
│  └─ findings.md       # key takeaways
├─ requirements.txt
└─ README.md
```

> Don’t worry if your repo doesn’t yet match this structure—use this README as a guide. You can keep only what you need.

---

## 🗂️ Dataset
You can use Kaggle’s **Titanic - Machine Learning from Disaster** dataset (`train.csv` / `test.csv`). Typical columns include:
- `Survived`, `Pclass`, `Sex`, `Age`, `SibSp`, `Parch`, `Fare`, `Embarked`, `Ticket`, `Cabin`, `Name`, `PassengerId`

Place CSVs in `data/raw/` as:
```
data/raw/train.csv
data/raw/test.csv   # optional
```

---

## ⚙️ Setup

### 1) Clone & create environment
```bash
git clone https://github.com/Sreyashisaha04/Titanic_EDA.git
cd Titanic_EDA

# (Option A) venv
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

# (Option B) conda
# conda create -n titanic-eda python=3.10 -y
# conda activate titanic-eda
```

### 2) Install dependencies
```bash
pip install -r requirements.txt
```

If you don’t have `requirements.txt` yet, use this minimal list:
```txt
pandas
numpy
matplotlib
seaborn
jupyter
plotly        # optional, for interactive charts
```
> Tip: run `pip freeze > requirements.txt` after you’re done to lock versions.

---

## ▶️ Quickstart

### Option A — Jupyter Notebook
1. Put `train.csv` in `data/raw/`.
2. Launch Jupyter and open the notebook:
   ```bash
   jupyter notebook notebooks/01_titanic_eda.ipynb
   ```
3. Run cells top‑to‑bottom. Charts will also be saved to `reports/figures/`.

### Option B — Python Scripts
Create a simple runner (example below) to clean and plot in one go:
```bash
python -m src.data --input data/raw/train.csv --out data/processed/train_clean.csv
python -m src.features --input data/processed/train_clean.csv --out data/processed/train_features.csv
python -m src.viz --input data/processed/train_features.csv --save-dir reports/figures
```

---

## 🧰 Example Utility Modules (drop‑in ready)

> Save these into `src/` to mirror the imports below.



## 📊 Analyses & Visuals
- **Data audit**: rows/cols, missing %, dtypes report.
- **Univariate**: histograms for Age, Fare; bar charts for Sex/Pclass/Embarked.
- **Bivariate**: survival by Sex, Pclass, Age bands, FamilySize/IsAlone, Embarked.
- **Feature engineering**: `Title`, `FamilySize`, `IsAlone`, `Deck`.
- **Exported PNGs** saved to `reports/figures/`.

> Optional: add Plotly versions for interactive exploration in a separate notebook.

---

## 📝 Interpreting Results (typical patterns)
- **Females** and **1st class** passengers have higher survival rates.
- **Children** show relatively higher survival than older adults.
- **Traveling alone** can correlate with lower survival than with family (depends on binning and definition).
- Ports of embarkation may show small distributional differences (context‑dependent).

> Treat these as hypotheses to test on your copy of the data—values vary with preprocessing choices.

---

## 🧪 Reproducibility
- All random operations (if any) should set a `random_state` in notebooks.
- Keep raw data immutable inside `data/raw/` and write outputs to `data/processed/`.
- Export all figures via `src/viz.py` so they can be regenerated.

---

## ✅ Checklist
- [ ] Place `train.csv` into `data/raw/`
- [ ] Create and activate a Python environment
- [ ] `pip install -r requirements.txt`
- [ ] Run the notebook or scripts
- [ ] Commit figures in `reports/figures/`
- [ ] Write short `reports/findings.md` with 5–8 bullet points

---

## 🤝 Contributing
Issues and PRs welcome—especially improvements to cleaning rules, better binning for age/fare, or new visualizations.

---

## 📄 License
MIT (or choose any license you prefer).

---

## 🙌 Acknowledgments
- Kaggle **Titanic: Machine Learning from Disaster** dataset.
- Pandas/NumPy/Matplotlib/Seaborn communities for excellent tools.
