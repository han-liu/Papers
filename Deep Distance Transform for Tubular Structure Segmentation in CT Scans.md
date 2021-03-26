##### [2021-03-24]
-  Deep Distance Transform for Tubular Structure Segmentation in CT Scans [[pdf]](https://arxiv.org/pdf/1912.03383.pdf) 
- *Yan Wang, Xu Wei, Fengze Liu, Jieneng Chen, Yuyin Zhou, Wei Shen, Elliot K Fishman, Alan L. Yuille*
- `2020, CVPR`

****

### Objective
Image segmentation (tubular structures)

### Proposed Method
A 3D network is used to produce (1) segmentation probability map and (2) distance map. The authors proposed to convert regression task to classification task by quantizing the distances to K bins. With the segmentation probability map and the quantized distance map, the final result can be reconstructed. Thresholding (T=0.98) was used to determine the skeleton of the segmentated object. For each pixel that belongs to the skeleton, Gaussian ball was created such that the mean was the x, y, z coordinate and the standard deviation is 1/3 of the predicted radii. Each Gaussian ball was then softened by a normalized factor and multiplied by the segmentation probability. The summation of all balls was then thresholded (T=0.5) to obtain the final result.

### Comments
- Very interesting paper to read. However, I believe the strong anatomical tubular shape prior has NOT been fully exploited. The only part using anatomical prior is the refinement process; this can be regarded as offline post-processing because the reconstructed shape was not involved in training process. The question is, can we enforce the tubular shape constraint during training? For example, the skeleton points (x, y, z) coordinates and their value, i.e., radii, should not vary between adjacent slices. (But is this implicitly resolved by 3D CNN? intra-slice information?)

- How reliable is it to obtain skeleton by thresholding? It seems quite challenging to use a high thresholding for thinning.

### My Version and the Difference
- Method: Given that I will be using distance maps to help tubular structure segmentation, I will design a 3D network to output the distance map (GT can be obtained from binary segmentation mask). Then, in each 2D slice (maybe best in the direction of the tube), the pixel with the largest distance value is considered skeleton point. One constraint would be (1) the position of skeleton points of adjacent slices should not change abrutply. Maybe this part can be implemented using DSNT. (2) Its value (radii of the circle) from adjacent slices should also not change abruptly due to anatomical constraint. These two constraints should be designed as losses to leverage the anatomical prior knowledge.

- Experiments: I will compare against (1) traditional methods for tubular structure segmentation (2) deep learning methods such as nn-Unet and other existing approaches. Since this method leverages anatomical information, ideally, this approach should acheive better results in HD, ASSD and hoefully better in Dice (though Dice is not a good metric to measure overall shape quality). 

- Differences
(1) convert regression of distance map to classification of quantized level. Accoding to this paper, it is unstable to train a regressor for distance maps but this needs to be validated through experiments. (2) A weight term on distance loss was designed to allow the classification loss to have similar property of regression loss, i.e., MSE. (3) reconstruct the 3D shape by creating a multi-variate Gaussian. I considered to process the shape in 2D manner and thus may be difficult to process the shape unless we can reliabily determine the skeleton direction.