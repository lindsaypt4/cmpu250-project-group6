`eurepoc_global_dataset_1_3.csv` is version 1.3 of the EuRepoC database, sourced
from [their website](https://eurepoc.eu/database/).

A _single_ extreme edge case, which was caused by a data entry failure from the
database authors, had to be corrected manually. In incident 3853,
`political_response_responding_actor` contains
`House Committee on Homeland Security Chairman Mark E. Green, MD (R-TN); USA`.
This value was replaced with
`House Committee on Homeland Security Chairman Mark E. Green, MD (R-TN), USA`.
That manually edited file is `eurepoc_global_dataset_1_3_EDITED.csv`.
