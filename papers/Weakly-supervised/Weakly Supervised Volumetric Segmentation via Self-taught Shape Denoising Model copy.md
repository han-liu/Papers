[2024-08-06]
- Weakly Supervised Object Detection in Chest X-Rays with Differentiable ROI Proposal Networks and Soft ROI Pooling [[pdf]](https://arxiv.org/abs/2402.11985) [[code]](https://github.com/philip-mueller/wsrpn)
- Philip Müller, Felix Meissen*, Georgios Kaissis, Daniel Rueckert*
- `2024, TMI`

****

### Objective
Generating bounding boxes for pathological findings in Chest X-rays with only classification labels

### Proposed Method
The proposed method is the first approach that directly optimize the box parameters for weakly-supervised object detection. The proposed method is built upon the MIL framework. The authors proposed another branch for ROIs, which are derived from the learnable embeddings (similar to DETR decoder), with cross-attention from Patch path (in DETR its cross-attention with image encoder). The authors proposed Gaussian ROI pool to estimate the box by mu and sigma. During training, the overall loss includes classification loss + supervised contrastive loss for each branch, and a consistency loss between two branches. 

### My version (before reading the details)
By looking at Fig. 1, the overall framework of the proposed method seems similar to the DETR-based approaches. In DETR, the output includes both classification and localization. In this weakly-supervised setting, since only classification labels are available, can we also use the DETR framework by training with only these labels without using localization ground truth? Previously, it has been known that the learnable query embeddings in the DETR correspond to 'anchors'. In this way, we can look up the probabilities of each embedding (box) and return the one with the highest probability. One more step is to ensure the embeddings are semantically meaningful, since now these boxes do not have the regularization from the localization ground truth. I will probably add a regularization loss to penalize the generated boxes that are outside of the input image. To further align the findings in the box and the classification label, I may also consider using ROI align and pooling layers to directly classify the proposals. This would be a combination of the DETR and the traditional region proposal-based methods. 

For experiments, I will compare against the previously methods including the MIL-based methods and CAM-based methods (CAM, Grad-CAM, etc.). I will also visualize different learnable embeddings to see what they correspond to.

### Comments

- For traditional methods, i.e., MIL- and CAM-based methods, the authors pointed out that these methods tended to assign higher scores to the most discriminative regions, instead of the entire objects.

- I did not expect the proposed method is a MIL-based method as it mentions its difference to MIL and CAM conceptually in Fig. 1. This makes me wonder how necessary for the framework to be built upon the MIL. Is it possible to use solely the DETR framework with minor modifications? This would make the framework more elegant and neat. It would be interesting for future research to explore this field.

- A metric for object detection for Chest X-rays named Robust Detection Outcome (RoDeO) is used.

- Interestingly, the box estimation is made by a Gaussian distribution. In the ablation study, the authors show that the performance is better when the estimated shape is Gaussian compared to a box-like distribution. But this may be because the Gaussian shapes are used for training.