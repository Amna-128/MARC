# MARC: Multi-Label Adaptive Retrieval Contrastive Loss for Remote Sensing Images

This repository contains the implementation of MARC (Multi-Label Adaptive Retrieval Contrastive Loss), 
a contrastive learning loss designed for multi-label remote sensing image retrieval.

MARC addresses challenges such as semantic overlap, class imbalance, and complex label co-occurrence 
by adaptively weighting sample pairs and dynamically adjusting the similarity temperature.



## Why MARC

Remote sensing images commonly contain multiple land-cover labels.  
Most contrastive learning methods assume single-label images or treat all positive pairs equally.  
This creates three problems:

1. Frequent classes dominate training.
2. Rare but important classes contribute very little.
3. Different levels of semantic overlap are ignored.

MARC introduces mechanisms that explicitly handle these challenges.

Pairwise Label Reweighting (PLR):
Rare and informative label co-occurrences receive stronger learning influence.

Dynamic Temperature Scaling (DTS):
The temperature used in contrastive learning adapts according to:
• how many labels two samples share
• how rare the anchor labels are

This produces more meaningful separations in the embedding space and improves retrieval performance.



## Key Features

✔️ Adaptive contrastive loss for multi-label data  
✔️ Balances frequent vs rare categories automatically  
✔️ Captures graded semantic overlap (not just match/no-match)  
✔️ Plug-and-play with CNN backbones (e.g., ResNet-18)  
✔️ Training cost similar to existing contrastive losses  
✔️ State-of-the-art retrieval performance on multiple benchmarks  



## Datasets

MARC is evaluated on three multi-label remote sensing datasets:

- **DLRSD** — high-resolution urban & natural scenes  
- **ML-AID** — multi-label version of AID  
- **WHDLD** — pixel-level labeled land-cover dataset  

Each dataset contains images with multiple co-occurring labels.



## Method Overview

Training phase:
1. Images are encoded by a backbone network and projection head.
2. Positive and negative sample relationships are created from labels.
3. PLR and DTS modify pair contributions inside the contrastive loss.

Retrieval phase:
1. The trained encoder generates embeddings.
2. Query and database embeddings are compared.
3. Images are ranked by similarity.
4. Labels are not needed during retrieval.



## Getting Started

Install dependencies:
pip install -r requirements.txt

Dataset structure:
datasets
  DLRSD
  MLAID
  WHDLD




## Results (Summary)

MARC and its weighted variant improve performance across evaluation metrics such as 
mean Average Precision, normalized Discounted Cumulative Gain, and weighted Average Precision.

Improvements are especially visible on rare classes and challenging retrieval cases.




## Contact

For questions or feedback, please open an issue in this repository.


