# Predictive_DT-NN_MR1-target

`MR1.ipynb`: decision tree / neural net classifiers discriminating MR1
binders, for:

**A machine learning approach to discriminate MR1 binders: The importance
of the phenol and carbonyl fragments**
https://www.sciencedirect.com/science/article/abs/pii/S0022286020307845?via%3Dihub

(The other publications previously listed here relate to other repos, not
this notebook.)

## Status

`MR1.ipynb` originally imported from a private module (`chemml`, later
renamed `chemsar`) that was never published — and note that public PyPI
also has an unrelated package also called `chemml`, so `pip install
chemml` would *not* get you the right thing even if it had been available.
That module has since become [mlmolprop](https://github.com/shamsaraj/mlmolprop),
a public, currently-maintained package, and this notebook has been ported
to it: every `chemml.<submodule>` import and several renamed function
parameters (see commit history) were updated to match mlmolprop's current
API.

**What's verified:** the ported code was executed end-to-end against a
small synthetic dataset (a handful of simple molecules, not real MR1
data) in a local `mlmolprop` conda environment. Molecule preparation,
descriptor generation, dataset processing, both classifier-fitting call
patterns (the loop over `lr`/`lsvm`/`kn` and the single `nn` model), and
plotting all ran successfully with no errors. Four cells hit issues
specific to that synthetic dataset being too small/simple rather than
translation bugs — confirmed by tracing each one to its actual cause:
- One cell regenerates the activity file from a `cat1` property embedded
  in the SDF itself; the synthetic SDF never had that property set.
- One cell selects a fixed list of named fragment descriptors
  (`fr_phenol`, etc.) that didn't survive feature selection on only 8
  synthetic molecules.
- Two cells (external test set prediction + Tanimoto similarity table)
  hit a scikit-learn feature-name mismatch, most likely from RDKit
  descriptors behaving inconsistently on such a tiny/chemically narrow
  toy set.

None of these are expected to be issues against the real, larger MR1
dataset this notebook was actually built for — but that data
(`data_MR1/all.sdf`, `ex_test.sdf`, `MR1.csv`) isn't included in this
repo, so it hasn't been possible to verify that directly.

**One pre-existing issue found, left as-is:** the LIME explanation call
near the end uses the default `mode="regression"` against a classifier.
It doesn't error, but it explains the raw predicted class label via
`.predict()` rather than the predicted probability via `.predict_proba()`
— likely not what was intended. This predates the port (the original
`lime2` call had the same default) so it's left unchanged rather than
silently reinterpreted; pass `mode="classification"` if you want the
probability-based explanation instead.

## Requirements

Python 3, [mlmolprop](https://github.com/shamsaraj/mlmolprop) (`conda env
create -f environment.yml && conda activate mlmolprop` from that repo),
RDKit, scikit-learn, LIME.

## Supplementary material.xlsx

Referenced by the notebook's markdown cells as background for the
modeling process and variable importance discussion.
