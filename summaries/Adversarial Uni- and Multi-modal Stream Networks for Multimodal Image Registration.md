[2021-04-12]
- Adversarial Uni- and Multi-modal Stream Networks for Multimodal Image Registration [[pdf]](https://arxiv.org/pdf/2007.02790.pdf) 
- Zhe Xu, Jie Luo, Jiangpeng Yan, Ritvik Pulya, Xiu Li, William Wells, and Jayender Jagadeesan*
- `2020, MICCAI`

****

### Objective
Multi-modal unsupervised image registration (from CT to MR)

### Proposed Method
(1) Train a 2D CycleGAN with MIND loss and identity loss for CT and MR translation. (2) Train a 3D Voxelmorph with separate encoders for real CT and fake MR, concat + 3D conv to obtain the final deformation field, apply the field to the CT image. Loss functions includes (1) SSIM between the deformed CT and real MR (2) smoothness term for deformation field.

![Alt text](https://github.com/han-liu/Papers/blob/master/figures/Adversarial%20Uni-%20and%20Multi-modal%20Stream%20Networks%20for%20Multimodal%20Image%20Registration.png?raw=true)


### Comments

- Similar to the I2I-based UDA methods, this paper shows that with additional input of translated uni-modal image, registration could be improved.

- The authors mentioned that 'After Uni- and Multi-model Stream networks, we obtain two deformation fields'. This statement is not correct because the total loss is only calculated regarding the final deformation field. In other words, without any regularization or losses, the so-called 'two deformation fields' do not have the physical meaning of deformation fields. Instead, they are only intermediate products used to create the final deformation field. Therefore, the experiments where the authors qualitatively compared the 'deformation fields' from uni-modal path and the fused field cannot be used to show the effectiveness of field fusion.

- Would it be possible to train GAN and VXM end-to-end? There are several papers building semgentation networks upon GAN but it seems that there was no work on the combination of registration and GAN.