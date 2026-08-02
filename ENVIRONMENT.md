# Environment

The analyses were run with:

- **R 4.5.1** (2025-06-13)

Key packages (versions used):

| Package | Version | Used for |
|---|---|---|
| data.table | 1.18.2 | reading the merged data (`fread`) |
| R.utils | 2.13.0 | lets `fread` read the `.csv.gz` data directly |
| dplyr / tidyr / purrr / stringr | 1.2.0 / 1.3.2 / 1.2.1 / — | data wrangling |
| jsonlite | 2.0.0 | parsing jsPsych survey responses (demographics) |
| broom | 1.0.12 | tidy t-test / correlation output |
| ggplot2 | 4.0.2 | figures |
| cowplot | 1.2.0 | multi-panel summary figures |
| lme4 | 2.0.1 | frequentist mixed models (checks) |
| brms | 2.23.0 | Bayesian logistic mixed-effects regressions |
| rstan | 2.32.7 | Stan backend for brms |
| bayestestR / parameters | 0.17.0 / 0.28.3 | posterior summaries / model tables |
| sjPlot | 2.9.0 | model tables |
| knitr / rmarkdown | 1.51 / 2.30 | notebook rendering |
| quantmod | 0.4.28 | GBP→USD conversion in the bonus report only (needs internet; not used for any reported statistic) |

Install everything with:

```r
install.packages(c(
  "data.table", "R.utils", "dplyr", "tidyr", "purrr", "stringr", "jsonlite",
  "broom", "ggplot2", "cowplot", "lme4", "brms", "bayestestR", "parameters",
  "sjPlot", "knitr", "rmarkdown", "quantmod"
))
```

`brms` compiles Stan models on first use and needs a working C++ toolchain
(macOS: Xcode command-line tools; Windows: Rtools). The Bayesian models in the
notebooks (4 chains × 4000 iterations) can take on the order of an hour each on
a laptop; fitted objects are cached as `.rds` files after the first run.
