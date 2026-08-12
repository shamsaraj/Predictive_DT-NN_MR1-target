# Predictive_DT-NN_MR1-target

`MR1.ipynb`: decision tree / neural net classifiers discriminating MR1
binders, for:

**A machine learning approach to discriminate MR1 binders: The importance
of the phenol and carbonyl fragments**
https://www.sciencedirect.com/science/article/abs/pii/S0022286020307845?via%3Dihub

```bibtex
@article{shamsara2020mr1,
  author  = {Shamsara, Jamal and Sch{\"u}{\"u}rmann, Gerrit},
  title   = {A machine learning approach to discriminate {MR1} binders: The importance of the phenol and carbonyl fragments},
  journal = {Journal of Molecular Structure},
  year    = {2020},
  volume  = {1217},
  pages   = {128459},
  doi     = {10.1016/j.molstruc.2020.128459}
}
```

Built on [mlmolprop](https://github.com/shamsaraj/mlmolprop).

## Requirements

Python 3, mlmolprop (`conda env create -f environment.yml && conda activate
mlmolprop` from that repo), RDKit, scikit-learn, LIME.

## Data

`data_MR1/` has the full training set (`all.sdf`, 71 compounds) and
external test set (`ex_test.sdf`, 19 compounds) from the paper's
supplementary table, with binder/non-binder labels in `MR1.csv`.
Structures resolved via PubChem, and for three compounds not on
PubChem, their bound-ligand structures in the RCSB PDB.

`Supplementary material.xlsx` is the paper's original supplementary
table (observed/predicted classes, full descriptor table, descriptor
definitions, variable importance, logistic regression model).
