# Predictive_DT-NN_MR1-target

`MR1.ipynb`: decision tree / neural net classifiers discriminating MR1
binders, for:

**A machine learning approach to discriminate MR1 binders: The importance
of the phenol and carbonyl fragments**
https://www.sciencedirect.com/science/article/abs/pii/S0022286020307845?via%3Dihub

Built on [mlmolprop](https://github.com/shamsaraj/mlmolprop).

## Requirements

Python 3, mlmolprop (`conda env create -f environment.yml && conda activate
mlmolprop` from that repo), RDKit, scikit-learn, LIME.

## Data

`data_MR1/` has the full training set (`all.sdf`, 71 compounds) and
external test set (`ex_test.sdf`, 19 compounds) from the paper's
supplementary table, with binder/non-binder labels in `MR1.csv`.
Structures: by PubChem CID where listed, by PubChem name lookup
otherwise (e.g. `6-FP` → 6-formylpterin, `5-OP-RU` →
5-(2-oxopropylideneamino)-6-D-ribitylaminouracil), and for `DA-6-FP`,
`2-AC-6-FP` (Ac-6-FP), and `HMB` from their bound-ligand structures in
the RCSB PDB (entries [5U17](https://www.rcsb.org/structure/5U17),
[4PJ5](https://www.rcsb.org/structure/4PJ5),
[5U2V](https://www.rcsb.org/structure/5U2V); ligand codes
`7WP`/`30W`/`7WQ`).

`Supplementary material.xlsx` is the paper's original supplementary
table (observed/predicted classes, full descriptor table, descriptor
definitions, variable importance, logistic regression model).
