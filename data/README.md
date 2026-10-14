`eurepoc_global_dataset_1_3.csv` is version 1.3 of the EuRepoC database, sourced
from [their website](https://eurepoc.eu/database/).

A _single_ extreme edge case, which was caused by a data entry failure from the
database authors, had to be corrected manually. In incident 3853,
`political_response_responding_actor` contains
`House Committee on Homeland Security Chairman Mark E. Green, MD (R-TN); USA`.
This value was replaced with
`House Committee on Homeland Security Chairman Mark E. Green, MD (R-TN), USA`.
That manually edited file is `eurepoc_global_dataset_1_3_EDITED.csv`.

# Data Codebook

Source: EuRepoC (European Repository of Cyber Incidents). Raw file: `eurepoc_raw.csv`.
Cleaned files: `eurepoc_clean.csv` (incident-level, 2017–2023), `pre_2020.csv`, `post_2020.csv`,
plus entity tables (`incident_type.csv`, `receiver.csv`, `initiator.csv`, ...) that join on `Incident`.
Missing values: "Not available" / "Not attributed" were recoded to blank (missing).

## eurepoc_clean.csv (one row per incident)
| Variable | Type | Description |
|---|---|---|
| Incident id | integer | Unique incident identifier; key linking all tables |
| Start date, End date | date | Incident start/end, parsed from dd.mm.yyyy |
| Year | integer | **Created.** Calendar year of Start date |
| Period | categorical | **Created.** "2017–2019" if Year < 2020, else "2020–2023" |
| Weighted intensity | numeric | EuRepoC intensity score adjusted by target multiplier [verify] |
| Impact score | numeric | EuRepoC impact indicator score |
| Data theft | categorical | Whether data theft occurred for private firms. Labeled as sensitive and non-sensitive |
| Disruption | categorical | Type/extent of disruption in percentage form |
| Functional impact | categorical | Functional impact level measure in days |

## incident_type.csv
| Incident | Incident id | Type | Category of incident; an incident may have several rows |

## receiver.csv
| Incident | Incident id | Category | Target sector (e.g. state institutions, critical infrastructure); multiple rows per incident |
| Region | Region of the target, one per row |

## Derived summary variables (in notebook)
| Incident Count | Number of recorded incidents per year |
| Incidents per Year | Period incident count divided by years in period (3 and 4) |
| Percentage | Share of period's incidents with a given type/category |
