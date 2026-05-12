# Introduction
This repository contains a project that attempts to re-implement the "Contrastive Decoding: Open-ended Text Generation as Optimization" paper by Xiang Lisa Li et al.. The paper introduces a new decoding method that improves strong model performance by penalizing the outputs that a weak model prefers, effectively "subtracting" common issues like repetition and topic drift

# Chosen Result

Our re-implementation focused on three key experiments from the original research:
### Experiment 1: Comparing Contrastive Decoding (CD) to other sampling methods, which is the paper's primary objective.
### Experiment 2: Studying the effect of relative model size on CD performance to determine optimal configurations.
### Experiment 3: Validating the V_head plausibility constraint and diversity-coherence trade-off, confirming α=0.1 as the optimal threshold for balancing MAUVE scores with lexical variety.

# GitHub Contents

code/: Re-implementation scripts, including 8-bit quantization and fp16 precision configurations.

data/: Instructions for obtaining Wikitext-103, CC-News, and PG-19 (used as a substitute for BookCorpus).

results/: Generated figures replicating OPT diagrams, log files, and comparison tables.

poster/: PDF of the in-class presentation poster.

report/: PDF of the final project report.

LICENSE: MIT License.

.gitignore: Standard Python and Git ignore rules.

# Re-implementation Details


# Reproduction Steps

To reproduce our results, ensure you have access to a GPU (L4 or A100 recommended). Install dependencies and run the provided scripts in the code/ directory. Note that the experiments utilize approximately 500 Google Colab compute units and require specific 8-bit quantization to fit larger expert models on a single GPU

# Results/Insights

# Conclusion

# References
Xiang Lisa Li, et al. "Contrastive Decoding: Open-ended Text Generation as Optimization".

Datasets: Wikitext-103, CC-News, and PG-19.

Tools: SimCSE, Hugging Face Transformers, and bitsandbytes for 8-bit quantization

# Acknowledgements
