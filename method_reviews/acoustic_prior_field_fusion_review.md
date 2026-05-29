# BirdCLEF+ 2026 | Acoustic Prior-Field Fusion

This is a Kaggle inference/fusion notebook with a leaderboard score around 0.949. It does not train a new model from scratch. Instead, it combines predictions from different model branches and applies prior-based post-processing to create the final submission.

The notebook mainly combines two branches:

| Branch | Weight |
|---|---:|
| yukiZ Perch/SSM branch | 0.0327 |
| Yaroslav v6 prior-field branch | 0.9673 |

Most of the final prediction comes from the v6 prior-field branch because it has the highest weight. The yukiZ Perch/SSM branch is included with a small weight to add diversity.

Inside the v6 branch, the notebook combines Proto/Perch-style predictions with SED-style predictions using rank-based blending. It then applies a prior-field adjustment using site-hour priors, temporal smoothing, file-level confidence, rank/power scaling, and residual corrections.

The notebook can also use BirdNET as an optional side correction. BirdNET is not used as a full model replacement; it is used as a small class-gated correction on top of the final prediction.

## Resources

Current notebook: https://www.kaggle.com/code/pilkwang/birdclef-2026-acoustic-prior-field-fusion