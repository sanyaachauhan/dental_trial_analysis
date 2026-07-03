# Dental Technology Trends in Clinical Trials

A reproducible analysis of emerging dental technology trends 
using registered clinical trial data from ClinicalTrials.gov.

## Research Question

Which dental technologies — implants, lasers, AI-assisted 
diagnosis, CAD/CAM workflows, teledentistry, and robotics — 
are being tested in registered clinical trials, and how has 
research activity changed over time?

## Key Findings

•⁠  ⁠*Dental implants* dominate with 1,285 trials — nearly 
25% of all dental research
•⁠  ⁠*AI-related trials* show near-zero activity before 2020, 
followed by rapid growth after 2021
•⁠  ⁠*Teledentistry* has only 10 trials despite widespread 
informal clinical use
•⁠  ⁠*Research is primarily academically funded*, unlike 
pharmaceutical research where industry dominates

## Data Source

ClinicalTrials.gov — U.S. federal registry of clinical studies 
worldwide. 4,422 dental trials analyzed (2000-2024).

## Methods

Trials were classified into technology categories using keyword 
detection across trial titles and summaries. Analysis conducted 
in R using tidyverse packages.

## Repository Structure

•⁠  ⁠⁠ scripts/ ⁠ — R scripts for import, classification, analysis, 
and visualization
•⁠  ⁠⁠ data/ ⁠ — Raw and processed datasets
•⁠  ⁠⁠ output/ ⁠ — Generated charts and figures
•⁠  ⁠⁠ Report.Rmd ⁠ — Full reproducible report
•⁠  ⁠⁠ Report.html ⁠ — Rendered HTML report

## Tools Used

R, tidyverse, ggplot2, janitor, lubridate

## Author

Dr.Sanya Chauhan — Dentist (BDS)
