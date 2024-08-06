[2022-06-22]
- Multi-organ Segmentation via Co-training Weight-averaged Models from Few-organ Datasets [[pdf]](https://arxiv.org/pdf/2008.07149.pdf) 
- *Rui Huang, Yuanjie Zheng, Zhiqiang Hu, Shaoting Zhang, Hongsheng Li*
- `2020, MICCAI`

****

### Objective
Medical image segmentation on partially-annotated datasets

### Paper
#### Motivation
Partially-labeled datasets extensive exist in medical image fields. How can we leverage such datasets to train a unified multi-class segmentation model?

#### Method
- Firstly, the authors train all single-organ (with annotations) segmentation models and use them to produce pseudo labels on unannotated datasets. In this way, we can have a pseudo-annotated multi-class dataset (hard labels).
- A co-training strategy was used to train two networks in parallel (same architecture but different intializations). 
	- With the hard labels, both networks are trained in a supervised manner (weighted focal loss + dice loss)
	- To regularize the noise injected by hard pseudo labels, the authors also use another loss to regularize the soft labels. 
		- For unannotated organs, masks are created by dilating the hard pseudo labels. These masks are applied to compute the soft losses.
		- The EMA of network weights is used since it can generate more robust online soft labels.
		- The soft pseudo labels produced by Network 1 are used to supervise the output predicted by Network 2. (just like CPS!)

- The weighted sum of these losses is used. Note that, there is an ramp-up weighting factor on the soft label loss, because at the beginning of the training, predictions from the networks may not be accurate.
- During inference, one of the EMA models, which shows better validation results, is used for inference.

#### Datasets
LiTs, KiTs, Pancreas, and MOBA (multi-organ dataset: 8 organs)

#### Compared Methods and Results
conditionCNN & Ablation study
metrics: mDice (slightly > cCNN), inference time (much quicker).

### Comments
- 2D network? 352 x 352 patch.
- Very similar to cross pseudo label supervision (CPS), the SOTA method in semi-supervised learning. This paper can be seen as another example that demonstrates the usefulness of CPS mechanism.
- The authors did not mentioned whether the hard pseudo labels are updated throughout the training process? So as the dilated masks. It seems not updated.
- I think the experiment settings of MOBA dataset are not reasonable. MOBA itself is a multi-organ dataset. "Specifically, the multi-organ segmentation masks are binarized and stored separately, i.e., we have manually constructed eight single-organ datasets." I'm not sure if the number of annotated organs within this dataset are different across subjects. If not, it is not clear why self-training (multi-class segmentation with pseudo labels) is better than combine (multi-class segmentation with real labels). "We speculate that it might result from the MOBA has more organs to segment and there is severe class imbalance among organs, and our framework can alleviate the imbalance problem by the proposed online-generated soft pseudo labels". It is not clear where this class imbalance problem comes from...
- Implemenetation details: quite interesting to see total number of epochs=10 and mini-batch=24 (3 per GPU x 8 GPUs).