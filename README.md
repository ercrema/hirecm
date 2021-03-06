
# Hierarchical Radiocarbon-dated Event Count (HiREC) Modelling
## Overview
This repo contains the data and R code used for the study presented in the following paper:

[*Carleton "Modelling Radiocarbon-dated event-count sequences with hierarchical Bayesian regression". DOI:10.31235/osf.io/mvt3b*](https://osf.io/preprints/socarxiv/mvt3b/)

## Abstract
Chronological uncertainty complicates attempts to use radiocarbon dates as proxies for processes like human population growth/decline, forest fires, and marine ingression. Established approaches involve turning databases of radiocarbon-date densities into single summary proxies that conflate process variation with chronological uncertainty. Here, I use simulated data to explore an alternate approach based on Bayesian hierarchical modeling---a Hierarchical Radiocarbon-dated Event Count (HiREC) Model. The approach involves assessing possible event sequences by bootstrap-sampling radiocarbon date densities and then using MCMC to estimate the parameters of an appropriate count-based regression model. The regressions based on individual bootstrapped sequences were nested within a hierarchical framework, which allowed for the estimation of super-population parameters that account for chronological uncertainty in the individual event times. Two processes were used to produce simulated data. One represented a simple monotonic change in event-counts and the other was based on a real palaeoclimate proxy record. In both cases, the method produced estimates that had the correct sign and were consistently biased toward zero. These results indicate that the approach is widely applicable and can produce useful results with as few as 1000 radiocarbon dates spanning 1000-year interval.

## Software
The R scripts contained in this repository are intended for replication efforts and to improve the transparency of my research. They are, of course, provided without warranty or technical support. That said, questions about the code can be directed to me, Chris Carleton, at ccarleton@protonmail.com.

### R
This analysis described in the associated manuscript was performed in R. Thus, you may need to download the latest version of [R](https://www.r-project.org/) in order to make use of the scripts described below.

### Nimble
This project made use of a Bayesian Analysis package called [Nimble](https://r-nimble.org/). See the Nimble website for documentation and a tutorial. Then, refer to the R scripts in this repo.


## Replication Outline
1. Generate simulated data
   * See `./R_scripts/Analysis/simdates_exp.R` and `./R_scripts/Analysis/simdates_palaeo.R`
   * For the latter, you will need to have the palaeoclimate dataset described in Kennett et al. Development and disintegration of maya political systems in response to climate change, Science 338 (2012) 788–791. doi:10.1126/science.1226299. I have included it in a .csv file in this repo at `/Data/Climate/`
   * These data generating scripts make use of the R package ['clam'](http://www.chrono.qub.ac.uk/blaauw/clam.html) to calibrate the dates.
2. Estimate model parameters with scripts that correspond to the data. There are several scripts with analytical functions in them. The ones used to estimate full HiREC models are labelled "negbin_hier..." while the core Negative Binomial regression can be run with just the "negbin.R" script. In the HiREC scripts there are lines that assign data to variables used in the Nimble code. Comment out the lines that don't apply before running the script---i.e., some lines are used to draw a single element from the radiocarbon-dated event count ensemble (see main paper) and others assign the chronological-error-free data to variables.

When using these scripts, pay close attention, of course, to path names, which may differ on your system.
