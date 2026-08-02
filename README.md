# When Is Complexity Avoided in Risky Choice? — Replication Package

Data and analysis code for the two-study project on **complexity aversion in
risky choice across the gain and loss domains** (Nie, Rieskamp, & Olschewski).
Participants repeatedly chose between a simple and a complex option — two risky
gambles in Study 1, a risky versus a sure option in Study 2 — separately in a
gain and a loss block. The package reproduces all behavioural results reported
in the paper: choice proportions, response-time effects, Bayesian logistic
mixed-effects regressions, subjective complexity/cognitive-uncertainty ratings
(Study 2), and cognitive-ability correlations.

Preregistrations:
- **Study 1:** https://doi.org/10.17605/OSF.IO/UYFWH
- **Study 2:** https://doi.org/10.17605/OSF.IO/T57HS

## Repository layout

```
project2_gainloss_replication/
├── README.md              ← this file (start here)
├── ENVIRONMENT.md         ← R and package versions
├── data/                  ← raw pre-exclusion data + stimulus tables
│   ├── study1/merged_data_study1.csv.gz
│   ├── study2/merged_data_study2.csv.gz
│   ├── stimuli/           ← lottery definitions used in each study (CSV)
│   └── README.md          ← column dictionary
├── 01_experiment/         ← example online experiment (jsPsych/JATOS)
└── 02_behavioural/        ← the full analysis notebooks (one per study)
```

## Data

`data/study{1,2}/merged_data_study{1,2}.csv.gz` contain the **complete,
pre-exclusion** trial-level data for all 150 participants per study — one row
per jsPsych event. The data contain no personal identifiers; participants are
identified by anonymous codes (`s1_p001`, …, `s2_p150`). **All participant and
trial exclusions reported in the paper are applied inside the analysis
notebooks** (`02_behavioural/`), so every exclusion step is reproducible from
these files.

`data/stimuli/` holds the lottery definition tables (outcomes, probabilities,
EV/SD/skew levels, and the arithmetic-expression components of the complex
format). See `data/README.md` for the column dictionary.

## How to reproduce

Install dependencies first — see **ENVIRONMENT.md**.

1. **Experiment** (`01_experiment/`) — the jsPsych experiment script (Study 2)
   as an example of the online experiments, documenting the task, instructions,
   and comprehension questions. Not needed to reproduce the analyses.
2. **Behavioural analyses** (`02_behavioural/`) — knit
   `study1_behavioural_analysis.Rmd` and `study2_behavioural_analysis.Rmd`
   from inside the `02_behavioural/` directory. Each notebook reads the data
   from `../data/`, applies the preregistered exclusions, and reproduces the
   statistics and figures of the corresponding study. Note: the Bayesian
   mixed-effects models (brms/Stan) take substantial time to fit.

## Scope

The package covers the full pipeline behind the reported results: experiment →
raw data → exclusions → behavioural analyses and figures. Downstream formatting
utilities (manuscript figure assembly beyond the notebook output, LaTeX tables)
are not included.
