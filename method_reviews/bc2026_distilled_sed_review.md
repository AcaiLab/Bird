# BirdCLEF+ 2026 | BC2026 Distilled-SED

This is a Kaggle train/inference notebook with a leaderboard score around 0.917. The method focuses on a mel-spectrogram SED model with Perch embedding distillation.

The main model is an EfficientNet-B0 backbone with a sound event detection attention head. Audio is converted into mel spectrograms, and the model makes both clip-level and frame-level predictions.

The key idea is to use Perch as a teacher model. During training, the notebook uses a distillation branch that tries to reproduce Perch’s 1536-dimensional audio embeddings using MSE loss. This helps the spectrogram model learn stronger audio representations while still training for bird classification.

At inference time, the Perch distillation branch is not used. The notebook uses the trained SED models exported to ONNX. It processes each 60-second soundscape as twelve 5-second windows, computes mel spectrograms, runs the ONNX fold models, and averages predictions across folds.

At a high level, the pipeline is:

- 5-second audio windows
- mel spectrograms
- EfficientNet-B0 backbone
- SED attention head
- Perch embedding distillation during training
- ONNX fold inference
- clip/frame prediction blending

This notebook is useful because it is a clearer mel-spectrogram / SED-based method compared with the ensemble and fusion notebooks. It also connects spectrogram-based classification with pretrained audio embeddings through distillation.

## Resources

Current notebook: https://www.kaggle.com/code/tuckerarrants/bc2026-distilled-sed

Referenced discussion:
https://www.kaggle.com/competitions/birdclef-2026/discussion/685318#3430354