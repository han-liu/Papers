[2022-06-25]
- Marginal loss and exclusion loss for partially supervised multi-organ segmentation [[pdf]](https://arxiv.org/pdf/2007.03868.pdf) 
- *Gonglei Shi, Li Xiao, Yang Chen, S. Kevin Zhou*
- `Medical Image Analysis 2020`

****

### Objective
Medical image segmentation on partially-annotated datasets

### Paper

#### Method
Two losses were proposed for partial label learninig: (1) marginal loss (2) exclusion loss.
- Marginal loss:
	- Treat voxels of unlabeled organs and background as a merged label (new class: label = 0). The probability summation of the channels of unlabeled organs and background is used as the supervision signal for model training. 
- Exclusion loss:
	- We expect that the intersection between the segmentation prediction pn from the network and en is as small as possible. For a network prediction of an unlabeled organ, the authors proposed to minimize its overlap with the labeled organs. This can avoid the conflict against the ground truth labels.

#### Datasets
BTCV (full annotation), Decathlon-liver (partial1 ), Decathlon-spleen (partial 2), Decathlon-pancreas (partial 3), KiTs kidney (partial 4).  

#### Compared Methods and Results
- Comparison against other losses:
	- Regular CE/Dice
	- marginal CE/Dice
	- exclusion CE/Dice
	- Combinations

- Comparisons against other partial label learning method
	- PaNN
	- PIPO-FAN

### Comments
- The exclusion loss is quite interesting as it considers the characteristic of the partial label learning. This can be considered as another example for PSL where real groundtruth and pseudo-labels are treated differently.
