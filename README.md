# Experiment Data for "Selecting SAT Encodings for Pseudo-Boolean and Linear Integer Constraints" in CP2022

This repository contains the constraint models and timing data for the experiments
in our paper.  The paper was written by Felix Ulrich-Oltean, Peter Nightingale and
James Walker, all from the University of York.  The paper was accepted to CP2022
in Haifa.

## Data
- The Essence Prime models and parameter files are in `bareproblems.tgz`.
- The extracted instance features are in `features-*.csv.gz` and the feature
  extraction times are in `fe-times-all.csv.gz`.
- Savile Row reports details of solving times, timeouts, etc. in `.info` files.
  The info files from all the timing runs have been aggregated in
  `infos.csv.gz`.
- `ml-setups` has the results from the different ML setups we tried. The
  information includes the predictions made, and the resulting simulated times.

## Software

### Savile Row
We used a modified version of Savile Row (included here) based on release 1.9.1,
additionally allowing the extraction of instance features.  The command-line
arguments required are `-sat-extract-f2f` for the fzn2feat features and
`-sat-extract-pb` for the pb-related features.  In the latter case, it's also
necessary to use `-sat-pb-XXX` and `-sat-sum-XXX` where XXX can be any of
mdd,gpw,ggt,swc.  This simply tells Savile Row that AMO-PB constraints can be
used, but the features are extracted before the actual SAT encoding is made, so
it doesn't matter which encoding you use on the command line for the purpose of
extracting features.

### Kissat
We used the
[sc-2021-sweep](https://github.com/arminbiere/kissat/tree/sc2021-sweep) version
of the Kissat SAT solver from Armin Biere's github repository.

### Python and libraries
The machine learning tasks were carried out using the `scikit-learn` library
(version 1.0.1) using Python 3.6.  Visualisations used seaborn and matplotlib.
