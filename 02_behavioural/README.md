# 02_behavioural — analysis notebooks

One R Markdown notebook per study. Each reads the shared pre-exclusion data
from `../data/`, applies the preregistered participant/trial exclusions, and
reproduces the behavioural results and figures of the paper.

| Notebook | Study | Reproduces |
|---|---|---|
| `study1_behavioural_analysis.Rmd` | Study 1 | complex/risky choice proportions and t-tests, RT differences, catch-trial accuracy, Bayesian logistic mixed-effects regression, CA correlations, summary figures |
| `study2_behavioural_analysis.Rmd` | Study 2 | complex/risky choice proportions and t-tests, RT differences, high-EV-trial accuracy, Bayesian regression, complexity/cognitive-uncertainty ratings, rating–choice correlations, CA correlations, summary figures |

**Exclusions applied inside the notebooks** (as preregistered): participants
with more than 8 total comprehension-question attempts; trials with RT < 1 s or
> 30 s; trials outside median ± 3 SD per participant × domain; participants
losing more than 50% of trials to these filters.

**How to run:** knit each notebook from inside this directory (the data paths
are relative: `../data/…`). Figures are written next to the notebooks. The
brms models (4 chains × 4000 iterations) are slow on first run and are cached
as `.rds` files; delete the `.rds` files to refit from scratch.
