# BirdCLEF+ 2026 | EoS.6 (bz)

This is a Kaggle inference/ensemble notebook with a leaderboard score around 0.949. It does not train one model from scratch. Instead, it combines outputs from several public notebooks and creates a final submission.

The final blend uses three model outputs:

| Model | LB Score | Weight |
|---|---:|---:|
| Model_21 | 0.928 | 0.014 |
| Model_52 | 0.949 | 0.021 |
| Model_74 | 0.949 | 0.965 |

Most of the final prediction comes from Model_74 because it has the highest weight. The other two models are included with very small weights.

The notebook combines approaches used in top Kaggle solutions. Some models use mel-spectrogram / SED-style audio classification, while another uses Perch audio embeddings with sequence models such as ProtoSSM/ResSSM. After generating predictions, the notebook blends them and applies post-processing such as smoothing, probability adjustment, and rank/power scaling.

## Resources

Current notebook: https://www.kaggle.com/code/dhyey654/birdclef-2026-eos-6-bz

Referenced notebooks:

- BC2026 Distilled-SED by Tucker Arrants
- Bird26 REPRODUCE Perch + ProtoSSM + ResSSM by yukiZ
- birdclef 2026 exp019 eos4 rank power 06 by Derek
- v6_0949_replay by Yaroslav Kholmirzayev
- Rank-Power Soundscape Fusion by Pilkwang Kim