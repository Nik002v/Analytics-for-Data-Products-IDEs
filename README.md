# Tool Window Usage Analysis

## Overview

This repository contains the analysis of tool window usage in an IDE. The goal of the analysis is to investigate whether there is a significant difference in how long a tool window stays open depending on whether it was opened manually or automatically.

For full methodology, results and discussion, see the
[project report](report.pdf).

### Dataset

The dataset is an event log tracking tool window activity. Each row contains:

- `user_id`: anonymized user ID
- `timestamp`: event time in epoch milliseconds
- `event_id`: "open" or "close"
- `open_type`: "manual" or "auto" (present only for open events)

The dataset may contain irregular logs, such as consecutive opens or closes, or missing closes due to forced IDE shutdowns.

### Task Description

The main objectives are:

1. Match open/close pairs to reconstruct sessions.
2. Calculate session durations.
3. Compare manual vs automatic sessions.
4. Determine statistical significance of the differences.

The analysis includes:

- Preprocessing and cleaning irregular logs
- Pairing open/close events per user
- Calculating session durations
- Visualizing distributions (histograms, boxplots, ECDF)
- Statistical testing (Mann–Whitney U test)

---

## Repository Contents

- `JB_PROJECT_IDE_.ipynb` – Jupyter Notebook with the full analysis (preprocessing, session reconstruction, visualization, statistics)
- `toolwindow_data - toolwindow_data.csv` – Original dataset used in the analysis
- `report.pdf` – Detailed report with methodology, results, and conclusions

---

## How to Run the Code

The notebook was created in **Google Colab**, so you can run it directly in your browser without any local setup.

### Steps:

1. Open the notebook in Google Colab:
   - Click on `JB_PROJECT_IDE_.ipynb` in this repository
   - Click **Open in Colab** (if prompted)
  
2. **Run the notebook cells:**
   - You can run all cells sequentially (`Runtime → Run all`) or step by step
   - The notebook will automatically preprocess the dataset, compute session durations, generate visualizations, and perform statistical tests, but first you must upload dataset
       
3. **Upload the dataset:**
   - In the notebook, there is a section labeled **"Upload Dataset"**
   - Click **Choose Files** and select `toolwindow_data - toolwindow_data.csv` from your computer
   - Wait for the file to finish uploading  

4. **View results:**
   - Summary tables and plots will be displayed inline
   - Statistical test results are included at the end

---

## Notes

- The notebook includes explanations and comments for each step of the analysis.
- The preprocessing handles irregular logs such as consecutive opens/closes or missing closes.
- The analysis focuses on the **Debug tool window**, which was chosen based on observed patterns of session durations.
- Manual sessions tend to be short (quick checks), whereas automatic sessions (triggered by debugging) are much longer.

---

## Requirements

If you want to run the notebook locally instead of Colab:

- Python 3.8+
- pandas
- numpy
- matplotlib
- seaborn
- scipy

Install dependencies using pip:

```bash
pip install pandas numpy matplotlib seaborn scipy
