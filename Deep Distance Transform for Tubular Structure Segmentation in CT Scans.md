##### [21-03-23]
-  Deep Distance Transform for Tubular Structure Segmentation in CT Scans [[pdf]](https://arxiv.org/pdf/1912.03383.pdf) 
- *Yan Wang, Xu Wei, Fengze Liu, Jieneng Chen, Yuyin Zhou, Wei Shen, Elliot K Fishman, Alan L. Yuille*
- `2020, CVPR`

****

### Technical problem:
Image segmentation (tubular structures)

### Methods


### Comments


### My version and the difference
- Method: Given that I will be using distance maps to help tubular structure segmentation, I will design a 3D network to output the distance map (GT can be obtained from binary segmentation mask). Then, in each 2D slice (maybe best in the direction of the tube), the pixel with the largest distance value is considered skeleton point. One constraint would be (1) the position of skeleton points of adjacent slices should not change abrutply. (2) Its value (radii of the circle) from adjacent slices should also not change abruptly due to anatomical constraint. These two constraints should be designed as losses to leverage the anatomical prior knowledge.

