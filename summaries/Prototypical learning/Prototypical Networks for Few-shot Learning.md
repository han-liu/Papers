[2021-04-01]
- Prototypical Networks for Few-shot Learning [[pdf]](https://arxiv.org/pdf/1703.05175.pdf) 
- *Jake Snell, Kevin Swersky, Richard S. Zemel*
- `2017, NIPS`

****

### Objective
Few/Zero-shot learning (FSL)

### Proposed Method
The authors proposed to address the overfitting issue in few-shot learning. For each class, prototypical network takes the mean feature vector of the support set in embedding space. The distance between incoming feature and the prototype is computed as the Bregman divergence, e.g., squared euclidean distance. Unlike classic classification networks, prototypical networks calculates the softmax probability using the feature distance rather than logits. During training, meta-learning is used to simulate the few-shot learning scenarios, e.g., we randomly select partial dataset from partial classes for meta-train and meta-test.

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Prototypical%20Networks%20for%20Few-shot%20Learning.png?raw=true)


### Comments
This is the original paper for prototypical networks, which seems received much attention recently. We've already seen several prototypical networks paper (most for UDA) in CVPR 2021. This also related to the uncertainty paper which considered the nearest distance (most similar class) to the class feature centroid as a metric; when the nearest distance is very large, this suggests that the input image might be an OOD regarding the training dataset.





