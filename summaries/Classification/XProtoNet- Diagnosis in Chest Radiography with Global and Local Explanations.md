[2021-03-31]
- XProtoNet: Diagnosis in Chest Radiography with Global and Local Explanations [[pdf]](https://arxiv.org/pdf/2103.10663.pdf) 
- *Eunji Kim, Siwon Kim, Minji Seo, Sungroh Yoon*
- `2021, CVPR`

****

### Objective
Prototypical learning for chest X-ray classification.

### Proposed Method
The focus of this paper is to use prototypical learning to determine the top K (K=3 in this paper) examples for each thoracic disease. Once we obtain the deep features from the feature module, C x K occurance maps (each is H x W and has a range between 0 and 1) are obtained and used as attention mask for further average pooling. The cosine similarities between K pooled feature vectors and K pre-computed prototypes are further used to produce the final predicted probability. Cluster loss is used to maximize the similarity for positive samples and minimize the similarity for negative samples. An affine transformation loss is used for regularization purpose (the disease sign should not change the relative position). Based on the results, the affine transformation loss improves the AUC score a lot. Lastly, L1 loss is used to make the occurance map sparse. 

Training scheme: 1) train the feature extractor of the ImageNet pretrained network for 5 epochs; 2) training the feature extractor and the prototype layer until the mean AUC score of the validation set does not improve for 3 epochs; 3) replacing the prototypes with the nearest feature vector from the training data; and 4) training the classification layer. 

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/XProtoNet%20Diagnosis%20in%20Chest%20Radiography%20with%20Global%20and%20Local%20Explanations.png?raw=true)


### Comments
- It is interesting to use prototypical network for better interpretability and this sounds like a reliable idea for disease explanation. I'm wondering the relationship between this line of prototypical learning and classic dictionary/codebook learning (feature space) and multi-atlas method (input image space). However, my concern is that K was set as 3 in the experiment. Does it mean the final classification network was trained with essentially 3 prototypes x 14 diseases images? If so, the results obtained by this method is amazing to me but does not seem to be very reasonable intuitively... 





