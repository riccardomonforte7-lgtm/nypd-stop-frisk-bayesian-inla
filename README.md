# NYPD Stop-and-Frisk Bayesian INLA

This project studies NYPD Stop, Question and Frisk data using Bayesian logistic regression models fitted with INLA in R.

The aim is to investigate which characteristics of the stop, the suspect, and the policing context are associated with the probability that a stop results in an arrest. The analysis also looks at whether there is residual variation across New York City boroughs and police command codes after accounting for observed stop-level covariates.

## Overview

The analysis uses the 2025 NYPD Stop, Question and Frisk dataset. The outcome variable is `SUSPECT_ARRESTED_FLAG`, which indicates whether the suspect was arrested after the stop.

The project focuses on a selected set of variables covering:

- suspect characteristics, such as age, sex, race, height, and weight;
- stop context, including how the stop was initiated, suspected crime, and stop duration;
- police actions during the stop, such as whether the suspect was frisked or searched;
- temporal information, based on the date and time of the stop;
- spatial information, using the New York City borough;
- police command code, used to explore residual variation across issuing commands.

The goal was not only to estimate associations with arrest probability, but also to compare increasingly structured Bayesian models.

## Models

Three Bayesian logistic regression models were fitted using INLA.

### Model 1: fixed-effects logistic regression

The first model is a baseline Bayesian logistic regression with fixed effects only. It estimates the association between observed suspect, stop, and policing-context variables and the probability of arrest.

### Model 2: temporal and spatial extension

The second model extends the baseline specification by adding structured temporal effects and a borough-level random effect.

This allows the model to account for variation across calendar dates, time of day, and New York City boroughs.

### Model 3: hierarchical command-level extension

The third model further extends Model 2 by adding a random intercept for `ISSUING_OFFICER_COMMAND_CODE`.

This accounts for residual heterogeneity across police command codes after adjusting for observed characteristics, temporal patterns, and borough-level variation.

## Model comparison

The models were compared using Bayesian model comparison and diagnostic criteria, including:

- DIC
- WAIC
- NLSCPO
- calibration plots based on grouped fitted probabilities

The hierarchical model with command-level random effects provided the best fit among the three specifications. The main fixed-effect results remained fairly stable across models, while the richer models captured additional residual structure in the data.

## Main findings

The analysis suggests that arrest probability is mainly associated with the suspected offence and with key features of the stop, especially whether the suspect was searched.

The results also suggest some residual variation across boroughs and clearer residual differences across police command codes. These findings should be interpreted as associations within an observational dataset, not as causal effects.

## Data

The dataset used in this project is included in the `data/` folder.

It contains NYPD Stop, Question and Frisk data for 2025. More details on the dataset source, variables used, and preprocessing steps are available in [`data/README.md`](data/README.md).

## Report

The final project report is available [here](report/S2882823_BDA.pdf).

The report contains the full model specification, prior choices, model comparison results, diagnostics, and interpretation of the main findings.

## Notes

This project was developed as part of a Bayesian Data Analysis assignment.

The focus was on specifying, fitting, comparing, and interpreting Bayesian logistic regression models for an observational dataset. The results should therefore be read as evidence of associations, not causal effects.
