# Brain-age-prediction

Predict age from brain grey matter (regression). Aging is associated with is grey matter (GM) atrophy, each year, an adult lose 0.1% of GM. We will try to learn a predictor of the chronological age (true age) using GM measurements on the brain on a population of healthy control participants.

Such a predictor provides the expected brain age of a subject. Deviation from this expected brain age indicates acceleration or slowdown of the aging process which may be associated with a pathological neurobiological process or protective factor of aging.

## Dataset
There are 357 samples in the training set and 90 samples in the test set.

## Input data
Voxel-based_morphometry VBM using cat12 software which provides:

Regions Of Interest (rois) of Grey Matter (GM) scaled for the Total Intracranial Volume (TIV): [train|test]_rois.csv 284 features.

VBM GM 3D maps or images (vbm3d) of voxels in the MNI space: [train|test]_vbm.npz contains 3D images of shapes (121, 145, 121). This npz contains the 3D mask and the affine transformation to MNI referential. Masking the brain provide flat 331 695 input features (voxels) for each participant.

By default problem.get_[train|test]_data() return the concatenation of 284 ROIs of Grey Matter (GM) features with 331 695 features (voxels) within a brain mask. Those two blocks are higly redundant. To select only on ROIs (rois) features do:

X[:, :284]
To select only on (vbm) (voxel with the brain) features do:

X[:, 284:]

## Target
The target can be found in [test|train]_participants.csv files, selecting the age column for regression problem.
