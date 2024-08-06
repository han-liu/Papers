[2021-04-15]
- Boundary IoU: Improving Object-Centric Image Segmentation Evaluation [[pdf]](https://arxiv.org/pdf/2103.16562.pdf) 
- *Bowen Cheng, Ross Girshick, Piotr Dollar, Alexander C. Berg, Alexander Kirillov*
- `2021, CVPR`
- [code](https://bowenc0221.github.io/boundary-iou/)

****

### Objective
New evaluation metric for segmentation.

### Proposed Method
A new evaluation metric Boundary IoU is proposed to better capture the segmentation error around the contours. This metric is not severely affected by the object size as mask IoU. However, this metric may not work well for the masks with holes inside the contours: it could yield a perfect score in these cases. Thus, the Boundary AP, which is the minimum of Boundary IoU and mask IoU, can be used since most of the boundary IoU values are smaller than the mask IoU.

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Boundary%20IoU.png?raw=true)


### Comments

- This metric can be very useful to capture subtle segmentation errors around boundary when the segmentation model is well trained. However, it may not be an appropriate metric at the beginning of the training.