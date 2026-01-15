Readme file for VE_FoI Project

Overview
--------
 - This contains the code for the paper “Association between COVID-19 Vaccine Efficacy and Force of Infection and Epidemic Force of Infection.”
 - The project links phase 3 double-blinded clinical trial data with daily force of infection (FoI) estimates from the Institute for Health Metrics and Evaluation (IHME). 
 By assigning site- and date-specific FoI estimates to participants, we investigate the relationship between vaccine efficacy (VE) and local force of infection.
 - Each R script corresponds to a specific trial and includes data linkage and modeling steps.

Data Sources 
------------
- 3 Phase 3 Vaccine Efficacy Trials
  * Individual participant data from randomized, double-blind trials in COVE, AZD1222 and ENSEMBLE

- Sitelist for the 3 Trials
  * Site location information

- IHME Force of Infection Estimates
  * Daily county-level FoI for U.S. counties
  * Daily state-level FoI for all U.S. states except Alaska (no trials in Alaska)
  * Daily country-level FoI for non-U.S. sites

- Due to data use agreements, the datasets cannot be shared publicly.

Data Linkage
------------
Step 1: Site Matching
- Link the trial data to the sitelist for each trial and extract the county name for each enrollment site
- For counties with unique names, match directly by county to the FoI dataset
- For counties with duplicate names (for example, "Orange County" in both California and Florida), match through both the county and state 
  names
- For the U.S. counties without FoI estimateds in the IHME dataset, use the corresponding state-level FoI data; for non-U.S. participants, 
  use country level data

Step 2: FoI Assignment and Time Series Construction
- Based on the participant site linked to the IHME dataset, obtain daily FoI estimates in calendar time throughouth each participant's follow-up period to enable location-specific daily FoI estimation.

Modeling
--------
- After linkage, we will fit a multivariate Cox proportional hazards model to assess the association between vaccine efficacy (VE) and the force of infection (FoI) 
through an interaction term. The model also incorporates time since enrollment to account for potential waning of vaccine protection. 
Analyses are conducted separately for each trial, with additional analyses restricted to U.S. participants in the AZD1222 and ENSEMBLE trials.

Contact
-------
For any question about this project, please contact jxu@fredhutch.org.

Last updated: 2026-01-12
