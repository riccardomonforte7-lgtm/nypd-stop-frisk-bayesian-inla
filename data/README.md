# Data

This folder contains the dataset used for the analysis.

The file `sqf-2025.xlsx` contains NYPD Stop, Question and Frisk data for 2025. The dataset is made publicly available by the New York City Police Department through its Stop, Question and Frisk data page.

## Dataset used

- `sqf-2025.xlsx`: NYPD Stop, Question and Frisk dataset for 2025

The analysis focuses on whether a stop results in an arrest. The main outcome variable is:

- `SUSPECT_ARRESTED_FLAG`

## Variables used in the analysis

The project uses a selected subset of variables related to the research questions, including:

- suspect characteristics;
- stop context and dynamics;
- police actions during the stop;
- temporal information;
- borough-level information;
- issuing officer command code.

Examples of variables used include:

- `SUSPECT_REPORTED_AGE`
- `SUSPECT_SEX`
- `SUSPECT_RACE_DESCRIPTION`
- `STOP_WAS_INITIATED`
- `SUSPECTED_CRIME_DESCRIPTION`
- `OBSERVED_DURATION_MINUTES`
- `STOP_DURATION_MINUTES`
- `WEAPON_FOUND_FLAG`
- `FRISKED_FLAG`
- `SEARCHED_FLAG`
- `STOP_FRISK_DATE`
- `STOP_FRISK_TIME`
- `STOP_LOCATION_BORO_NAME`
- `ISSUING_OFFICER_COMMAND_CODE`

## Preprocessing

The preprocessing steps are implemented in the main R Markdown file.

The main steps include:

- selecting variables relevant to the research questions;
- checking for duplicate records using `STOP_ID`;
- converting `(null)` entries to `NA`;
- removing observations with missing values in the selected variables;
- encoding categorical variables as factors;
- grouping rare `SUSPECTED_CRIME_DESCRIPTION` levels into an `OTHER` category;
- applying `log(1 + x)` transformations to highly right-skewed duration variables;
- creating date and time variables used in the temporal components of the Bayesian models.

## Notes

The dataset is included here to make the analysis easier to reproduce. The data are not owned by this repository and should be understood as the public NYPD source dataset used for the project.

For the official source and documentation, please refer to the NYPD Stop, Question and Frisk data page.
