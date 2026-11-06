# ECON-3916-LAB14
# OLS Diagnostics: When the Standard Error Is Lying

## Objective
I examined how heteroskedasticity, outliers, and influential observations affect OLS standard errors and inference, and tested whether robust standard errors and regression diagnostics improve the reliability of my results.

## Methodology
- Simulated heteroskedastic data where the error variance increased with x, then fitted OLS using both classical and HC3 robust standard errors.
- Ran 400 Monte Carlo simulations to compare the coverage rates of classical and robust 95% confidence intervals and calculated their Monte Carlo standard errors.
- Examined four residual plots alongside Breusch-Pagan and Jarque-Bera tests to identify heteroskedasticity, non-normality, and unusual observations.
- Measured the influence of an individual observation by removing one row from a 600-observation dataset and comparing the slope and standard error before and after deletion.
- Fitted an OLS regression using California Housing data and compared classical and HC3 standard errors for AveRooms.
- Implemented `hc3_se()` to calculate robust standard errors and compared results with all districts against results excluding the 965 districts at the 5.0 housing-value ceiling.
- **Optional extension:** Used Cook's distance to examine how much influence was concentrated in five districts.
- **Optional challenge:** Investigated a regression that passed standard diagnostic tests despite being incorrectly specified.

## Key Findings
- **Heteroskedasticity:** The estimated slope was unchanged when I switched from classical to HC3 standard errors. This showed me that changing the covariance estimator affects uncertainty estimates, not the fitted OLS coefficients.
- **Confidence interval coverage:** Across 400 simulated samples, I compared how often classical and robust 95% confidence intervals contained the true slope. I used Monte Carlo standard errors to assess the uncertainty in the estimated coverage rates.
- **Regression diagnostics:** The residual plots, Breusch-Pagan test, and Jarque-Bera test provided different information about the model's assumptions. I learned that no single diagnostic is enough to evaluate a regression.
- **Influential observations:** Removing just one observation from a dataset of 600 changed the slope relative to its standard error and reduced the estimated standard error. This demonstrated how an influential observation can affect inference.
- **California Housing:** The HC3-to-classical standard error comparison for AveRooms showed how the choice of standard error estimator matters in real data.
- **HC3 implementation:** My `hc3_se()` function let me compare the robust standard error for AveRooms before and after excluding the 965 districts at the 5.0 ceiling.
- **Optional extension:** Cook's distance helped me assess whether a small group of districts accounted for a disproportionate share of influence.
- **Optional challenge:** A regression can pass standard diagnostic checks and still be wrong if the underlying model is misspecified.

## Takeaway
I learned that a regression coefficient alone does not tell me how reliable an estimate is. Classical standard errors can be misleading under heteroskedasticity, while HC3 provides a way to make inference more robust to nonconstant error variance. I also saw why checking residuals, influential observations, and model specification matters before trusting regression results.
