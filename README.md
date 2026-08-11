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

`data_MR1/` has the training set (`all.sdf`, 63 compounds) and external
test set (`ex_test.sdf`, 17 compounds), with binder/non-binder labels in
`MR1.csv`. Structures and labels are reconstructed from the paper's
supplementary table via PubChem CID lookup. 10 of the original 90
compounds (e.g. `6-FP`, `5-OP-RU`) use MR1-ligand nomenclature specific to
the immunology literature rather than a resolvable identifier, so
they're not included here.

`Supplementary material.xlsx` is the paper's original supplementary
table (observed/predicted classes, full descriptor table, descriptor
definitions, variable importance, logistic regression model).
