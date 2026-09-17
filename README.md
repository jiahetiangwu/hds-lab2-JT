# HDS Lab 2: Mayo Clinic PBC Trial Survival Analysis

This repository contains my Lab 2 submission for PUBH 6854 Applied Computing in Health Data Science.

## Research Question

Among randomized participants in the Mayo Clinic Primary Biliary Cirrhosis (PBC) trial, was there evidence of a difference in survival between the D-penicillamine and placebo treatment groups?

## Analysis

The analysis was implemented independently in both Python and R using the same dataset and research question. The workflow:

* loads the PBC data directly from the original public source;
* restricts the analysis to randomized participants with known treatment assignments;
* creates a binary event indicator for death;
* summarizes participants and deaths by treatment group;
* estimates Kaplan-Meier survival curves; and
* compares the survival distributions using a log-rank test.

## Repository Structure

```text
hds-lab2-JT/
├── README.md
├── AI_USAGE.md
├── environment.yml
└── notebooks/
    ├── pbc_analysis_python.ipynb
    ├── pbc_analysis_python.html
    ├── pbc_analysis_r.Rmd
    └── pbc_analysis_r.html
```

## Data Source

The analysis uses the Mayo Clinic Primary Biliary Cirrhosis (PBC) trial dataset from the `survival` R package, accessed through the Rdatasets repository.

Both implementations load the data directly from the public source:

```text
https://vincentarelbundock.github.io/Rdatasets/csv/survival/pbc.csv
```

No manually cleaned local copy of the dataset is required.

## Python Environment

The Python environment is documented in `environment.yml`.

To create the environment:

```bash
conda env create -f environment.yml
```

Then activate it:

```bash
conda activate hds-lab2-JT
```

## Running the Python Notebook

From the repository root, activate the conda environment and launch JupyterLab:

```bash
conda activate hds-lab2-JT
jupyter lab
```

Open:

```text
notebooks/pbc_analysis_python.ipynb
```

Then select **Kernel → Restart Kernel and Run All Cells**.

The notebook should run from top to bottom without manual intervention because the data are downloaded directly from the public source.

A rendered version is provided at:

```text
notebooks/pbc_analysis_python.html
```
## R Environment

The R analysis requires the `survival` package.

For reproducibility, the R Markdown file automatically checks whether `survival` is installed. If the package is not available, the script installs it from CRAN before loading it. Therefore, no manual installation of `survival` is required before running the analysis.

An internet connection is required to download the PBC dataset and, if necessary, install the `survival` package.

A standard R environment capable of rendering R Markdown documents is assumed to be available.

## Running the R Markdown Analysis


Open:

```text
notebooks/pbc_analysis_r.Rmd
```

in RStudio and select **Knit**, or render it from R with:

```r
rmarkdown::render("notebooks/pbc_analysis_r.Rmd")
```

A rendered version is provided at:

```text
notebooks/pbc_analysis_r.html
```

## Results

The Python and R implementations produced consistent results. The Kaplan-Meier survival curves were broadly similar between the D-penicillamine and placebo groups, and the log-rank test did not show a statistically significant difference in survival between the treatment groups (p = 0.75).

## AI Assistance

Generative AI assistance used during this assignment is documented in `AI_USAGE.md` and at the relevant locations within the analysis notebooks.
