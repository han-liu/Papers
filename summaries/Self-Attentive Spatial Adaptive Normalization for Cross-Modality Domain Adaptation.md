##### [2021-04-07]
- Self-Attentive Spatial Adaptive Normalization for Cross-Modality Domain Adaptation [[pdf]](https://arxiv.org/pdf/2103.03781.pdf) 
- *Devavrat Tomar, Manana Lortkipanidze, Guillaume Vray, Behzad Bozorgtabar, Jean-Philippe Thiran*
- `2021, TMI`

****

### Objective
UDA unpaired image segmentation.

### Proposed Method
A 3D network is used to produce (1) segmentation probability map and (2) distance map. The authors proposed to convert regression task to classification task by quantizing the distances to K bins. With the segmentation probability map and the quantized distance map, the final result can be reconstructed. Thresholding (T=0.98) was used to determine the skeleton of the segmentated object. For each pixel that belongs to the skeleton, Gaussian ball was created such that the mean was the x, y, z coordinate and the standard deviation is 1/3 of the predicted radii. Each Gaussian ball was then softened by a normalized factor and multiplied by the segmentation probability. The summation of all balls was then thresholded (T=0.5) to obtain the final result.

![alt text]()

### Comments
- UDA with image synthesisSynSeg 