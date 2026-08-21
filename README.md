# AI-Guided Protein Engineering

### Benchmarking Protein Language Models for Mutation Fitness Prediction

This project investigates the use of machine learning and pretrained protein
language models for predicting and ranking experimentally measured protein
mutations.

Experimental protein mutation data were obtained from ProteinGym, a benchmark
containing deep mutational scanning datasets.

## Objective

The goal was to evaluate whether representations learned by the ESM-2 protein
language model could predict protein mutation fitness and help prioritize
promising variants for experimental testing.

## Workflow

ProteinGym Experimental Data  
↓  
Protein Variant Sequences  
↓  
ESM-2 Protein Language Model  
↓  
320-Dimensional Protein Embeddings  
↓  
Random Forest Regression  
↓  
Mutation Fitness Prediction  
↓  
Variant Ranking  

A second model using interpretable mutation-level features was developed as a
baseline comparison.

## Technologies

- Python
- PyTorch
- Hugging Face Transformers
- ESM-2
- Scikit-learn
- Pandas
- NumPy
- SciPy
- Matplotlib
- ProteinGym

## Results

| Model | MAE | RMSE | R² | Spearman |
|---|---:|---:|---:|---:|
| ESM-2 + Random Forest | 1.0017 | 1.3163 | 0.5043 | 0.6246 |
| Mutation Features + Random Forest | 0.5525 | 0.9000 | 0.7683 | 0.8726 |

The interpretable mutation-feature model significantly outperformed pooled
ESM-2 sequence embeddings on this assay.

The ESM-based ranking model nevertheless showed strong enrichment for
high-performing mutations. The top 20 AI-ranked variants had an average
experimental DMS score of 0.8648 compared with -0.6647 across the full
held-out test set.

## Key Finding

A major finding was that greater model complexity did not automatically lead
to better predictive performance.

Simple mutation-level features provided stronger predictions than pooled
ESM-2 sequence representations for this dataset, demonstrating the importance
of benchmarking advanced protein AI methods against strong baselines.

## Applications

This type of computational workflow could be used as an early-stage screening
tool to prioritize protein variants before expensive laboratory experiments.

Potential extensions include:

- Antibody sequence optimization
- Protein stability prediction
- Binding affinity prediction
- ProteinMPNN candidate generation
- Structure prediction using Boltz or AlphaFold
- Multi-objective therapeutic protein optimization

## Disclaimer

This project is a computational proof of concept intended for research and
educational purposes. Model predictions are not experimentally validated
therapeutic designs.
