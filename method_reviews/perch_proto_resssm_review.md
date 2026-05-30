# Bird26 | REPRODUCE | Perch + ProtoSSM + ResSSM | INF/TRAIN

This is a Kaggle notebook with a reported leaderboard score around 0.928. Unlike the previous ensemble/fusion notebooks, this one is more focused on a specific modeling approach: using pretrained Perch audio embeddings with sequence models.

The notebook can support both training and inference. In the run I tested, it was in submit mode, so it loaded pretrained ProtoSSM and ResidualSSM weights instead of training them from scratch.

At a high level, the pipeline is:
1. Use Perch v2 to extract predictions and 1536-dimensional audio embeddings from 5-second soundscape windows.
2. Group the windows into 60-second soundscape files with 12 windows per file.
3. Use ProtoSSM to model temporal patterns across the 12 windows.
4. Use MLP probes on PCA-reduced Perch embeddings as an additional prediction branch.
5. Use ResidualSSM as a second-pass correction model.
6. Apply post-processing such as temporal shift TTA, per-taxon temperature scaling, file-level confidence scaling, rank-aware scaling, delta smoothing, and threshold sharpening.

This notebook is useful because it directly connects to the idea of using pretrained audio embeddings and training a model on top of them. It is less about blending many public submissions and more about using Perch embeddings with sequence modeling.

## Resources

Current notebook: https://www.kaggle.com/code/hideyukizushi/bird26-reproduce-perch-protossm-resssm-inf-train