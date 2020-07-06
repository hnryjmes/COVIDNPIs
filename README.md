# COVID-19 Countermeasure Effectiveness

This repo contains the code used for [Brauner et al. *The effectiveness and perceived burden of nonpharmaceutical interventions against COVID-19 transmission: a modelling study with 41 countries* (2020)](https://www.medrxiv.org/content/10.1101/2020.05.28.20116129v2.article-info)

## Install

* [Get Poetry](https://python-poetry.org/docs/#installation)
* Clone this repository.
* Install the dependencies and this lib `poetry install` (creates a virtual env by default).

## Reproducibility
`scripts/run_add_exps.sh` is used to run "additional" validation experiments, and this file saves full model traces as pickle files (these end up being quite large files). The experiments run are:

1. Additive model. 
2. Noisy-R model. 
3. Different-effects model (each NPI has a different effectiveness in each country).
3. A noisy discrete-renewal model. 
4. Inclusion of OxCGRT Travel NPIs. 
5. Inclusion of OxCGRT public transport NPI. 
5. Inclusion of OxCGRT internal movement NPI. 
5. Inclusion of OxCGRT information campaign NPI. 
5. Inclusion of OxCGRT symptomatic testing NPI. 
5. Inclusion of bonus NPI indicating the onset of intervention.
5. Estimating the effecting using the timing of each NPI i.e., the n-th NPI is used rather than the specific NPI . 
5. Different delays in countries that had symptomatic testing. 
5. Delaying schools and universities by approx. 1 generation interval. 
5. Performing aggregrated holdouts. 
5. Cases only model. 
6. Deaths only model. 

`scripts/run_ho_exps.sh` is used to perform holdout experiment. Custom `ResultsObject` pickle files are saved with data pertaining to the estimated NPI effectiveness and predictions for the unseen countries. We mask cases after the first 14 days of cases (likewise for deaths). 

See `notebooks/double-entry-data` for plotting code (plotting notebooks have `_plotter` in their name). Additionally, the file `final_results.ipynb` is used to peform a full run. 

`notebooks/double-entry-data/double_entry_final.csv` has the final CSV used for the code. 
