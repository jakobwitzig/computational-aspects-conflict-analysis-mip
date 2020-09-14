## Online Supplement of:

# *Computational Aspects of Infeasibility Analysis in Mixed Integer Programming*

##### Jakob Witzig <sup>1</sup>, Timo Berthold<sup>2</sup>, and Stefan Heinz<sup>3</sup>

###### <sup>1</sup> Zuse Institute Berlin, Takustr. 7, 14195 Berlin, <witzig@zib.de>

###### <sup>2</sup> Fair Isaac Germany GmbH, Stubenwald-Allee 19, 64625 Bensheim, <timoberthold@fico.com>

###### <sup>3</sup> Gurobi GmbH, Ulmenstr. 37-39, 60325 Frankfurt am Main, <heinz@gurobi.com>
___

This online supplement provides tables in CSV format with detailed results of the computational experiments conducted for the paper "Computational Aspects of Infeasibility Analysis in Mixed Integer Programming".
A preprint is available as technical repprt published by Zuse Institute Berlin, 2019.

As test set we used MIPLIB 2017 (https://miplib.zib.de/).

To address performance variability, all experiments were run with three different random seeds. All data provided in this repository represents data where all settings considered in a respective experiment finished without error (e.g., numerical violations). Thus, for some instance less than three observations are available.

For every experiment we provide CSV files containing
- all instances that finished without numerical issues (`*_clean.csv`)
- the subset of affected instances (`*_affected.csv`)
___
### Experiments

The following experiments where conducted:
* SCIP without LP-based infeasibility analysis (baseline) compared to LP-based conflict graph analysis, dual proof analysis and a simultaneous approach of LP-based conflict graph and dual proof analysis (`overview/MIPLIB2017_supplement_overview_complete_*.csv`)
* SCIP using a simultaneous approach of LP-based conflict graph and dual proof analysis w/ and w/o
   * nonzero cancellation by using variable bounds (`presolving_strengthening/nnz-cancellation/MIPLIB2017_supplement_nnz_cancellation*.csv`)
   * nonzero cancellation by using variable bound constraints (`presolving_strengthening/vbounds/MIPLIB2017_supplement_vbound*.csv`)
   * all three techniques above (`presolving_strengthening/MIPLIB2017_supplement_presolving_*.csv`)
   * updating procedure of dual proof constraints derived from bound exceeding LP relaxations (`presolving_strengthening/update-boundex/MIPLIB2017_supplement_update_boundex*.csv`)
   * separating c-MIR inequalities based on dual proof constraints (`mir/MIPLIB2017_supplement_mir*.csv`)
   * a filtering procedure for dual proof constraints (`filtering/MIPLIB2017_supplement_filtering*.csv`)
* SCIP using a simultaneous approach of LP-based conflict graph and dual proof analysis w/ and w/o all newly developed techniques presented in this paper (`disabled-features/MIPLIB2017_supplement_disabled_features*.csv`)

#### NLP-based branch-and-bound:
* SCIP w/o conflict analysis at all vs. enabled conflict graph analysis due to propagation vs. enabled NLP-based dual proof analysis (`nlp-based/MINLP_discrete_local_dual_proofs_all.csv`)
___
### CSV data details

All instance features, e.g., solving time or explored tree nodes, are always given with respect to a setting `s`:

* `noLPinf` : SCIP without analyzing infeasibilties derived from the LP relaxation
* `confgraph` : SCIP applying conflict graph analysis solely when analyzing infeasibilities derived from the LP relaxation
* `dualproof` : SCIP applying dual proof analysis solely when analyzing infeasibilities derived from the LP relaxation
* `combined` : SCIP using both conflict graph and dual proof analysis when analyzing infeasibilities derived from the LP relaxation

#### Used instance features

* `ProblemName` : The name of the instance
* `T_s` : Absolute solving time in seconds
* `TQ_s` : Relative solving time
* `N_s` : Absolute number of explored tree nodes
* `NQ_s` : Relative number of explored tree nodes
* `DI_s` : Absolute dual integral
* `DIQ_s` : Relative dual integral
* `Gap_s` : Absolute gap
* `GapQ_s` : Relative gap

___
### How to Cite?

```
@techreport{WitzigBertholdHeinz2019,
  author      = {Jakob Witzig and Timo Berthold and Stefan Heinz},
  title       = {Computational Aspects of Infeasibility Analysis in Mixed Integer Programming},
  institution = {ZIB},
  address     = {Takustr.~7, 14195 Berlin},
  number      = {19-54},
  language    = {eng},
  urn         = {urn:nbn:de:0297-zib-74962},
  year        = {2019}
}
```