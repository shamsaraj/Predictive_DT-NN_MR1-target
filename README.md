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

`data_MR1/` has the training set (`all.sdf`, 71 compounds) and external
test set (`ex_test.sdf`, 18 compounds), with binder/non-binder labels in
`MR1.csv`. Structures and labels are reconstructed from the paper's
supplementary table: by PubChem CID where listed, by PubChem name lookup
otherwise (e.g. `6-FP` → 6-formylpterin, `5-OP-RU` →
5-(2-oxopropylideneamino)-6-D-ribitylaminouracil), and for `DA-6-FP` /
`2-AC-6-FP` (Ac-6-FP) from their bound-ligand structures in the RCSB PDB
(entries [5U17](https://www.rcsb.org/structure/5U17) and
[4PJ5](https://www.rcsb.org/structure/4PJ5), ligand codes `7WP`/`30W`).
`HMB` (1 of the original 90 compounds) doesn't resolve to a confirmed
structure under any name tried, so it's not included.

`Supplementary material.xlsx` is the paper's original supplementary
table (observed/predicted classes, full descriptor table, descriptor
definitions, variable importance, logistic regression model).
