# Introduction
This repository contains a project that attempts to re-implement the "Contrastive Decoding: Open-ended Text Generation as Optimization" paper by Xiang Lisa Li et al.. The paper introduces a new decoding method that improves strong model performance by penalizing the outputs that a weak model prefers, effectively "subtracting" common issues like repetition and topic drift

# Chosen Result

Our re-implementation focused on three key experiments from the original research:
### Experiment 1: 
Comparing Contrastive Decoding (CD) to other sampling methods, which is the paper's primary objective.
### Experiment 2: 
Studying the effect of relative model size on CD performance to determine optimal configurations.
### Experiment 3: 
Validating the V_head plausibility constraint and diversity-coherence trade-off, confirming α=0.1 as the optimal threshold for balancing MAUVE scores with lexical variety.

# GitHub Contents

code/: Re-implementation scripts, including 8-bit quantization and fp16 precision configurations.

data/: Instructions for obtaining Wikitext-103, CC-News, and PG-19 (used as a substitute for BookCorpus).

results/: Generated figures replicating OPT diagrams, log files, and comparison tables.

poster/: PDF of the in-class presentation poster.

report/: PDF of the final project report.

LICENSE: MIT License.

.gitignore: Standard Python and Git ignore rules.

# Re-implementation Details
We kept our approach as true to the paper as possible, making the following adjustments to accomadate resource constraints:
- Quantized OPT models, substituted OPT6.7B for OPT13B 
- Smaller evaluation sample sizes (~100 prompts)
- Dataset substitutions (PG-19 instead of BookCorpus)
- Used CD-greedy decoding instead of CD-Beam

# Reproduction Steps

To reproduce our results, ensure you have access to a GPU (L4 or A100 recommended). Download or Google Colab file from the `code` directory, and run the cells in order. 

*Note: GPT and OPT experiments cannot be run concurrently in the same session

- Choose one model family to load
- Double check that the correct model and hyperparmeters for the current model family are being referenced in each cell
  - (tau = 0.5 for GPT, tau = 1 for OPT)
- Run all code cells in order
- Then load the other model family and repeat

*Note: Running all experiments utilizes approximately 500 Google Colab compute units on an A100 GPU.

# Results/Insights
Our repository reliably demonstrates the core behavior of Contrastive Decoding and provides a practical framework for reproducing and experimenting with the method. Users can expect:
- Reproducible CD experiments across GPT-2 and OPT families
- Evaluation pipelines for Diversity, Coherence, and MAUVE
- Hyperparameter sweeps over α and model pairings

While our overall trends aligned closely with the original results, some metric magnitudes (particularly MAUVE) were lower and more variable. We attribute this primarily changes we mentioned in `Re-implementation Details`

# Conclusion
We succesfully validated Contrastive Decoding's competitive performance against existing popular decoding methods and verified other design choices made by the paper.

# References
Xiang Lisa Li, et al. "Contrastive Decoding: Open-ended Text Generation as Optimization".

Datasets: Wikitext-103, CC-News, and PG-19.

Tools: SimCSE, Hugging Face Transformers, and bitsandbytes for 8-bit quantization

# Acknowledgements
Thank you to Professor Kilian Weinberger and Professor Wei-chiu Ma, as well as the course staff of CS4782 at Cornell University for supporting our education and completion of this project!
