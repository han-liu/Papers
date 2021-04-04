[2021-03-29]
- HAD-Net: A Hierarchical Adversarial Knowledge Distillation Network for Improved Enhanced Tumour Segmentation Without Post-Contrast Images [[pdf]](https://openreview.net/pdf?id=48UgSFrNR2) 
- *Saverio Vadacchino, Raghav Mehta, Nazanin Mohammadi Sepahvand, Brennan Nichyporuk, James J Clark, Tal Arbel*
- `2021, MIDL`

****

### Objective
Knowledge distillation for missing modality (without post-contrast T1 images in Brats dataset)

### Proposed Method
The proposed method is based on the Teacher-student model and is very similar to [KD-Net](https://link.springer.com/content/pdf/10.1007%2F978-3-030-59710-8_75.pdf) from MICCAI 2020. The difference is (1) instead of directly computing the KL loss of latent space features and KD loss (dice + BCE) between binary teacher prediction and student prediction as in KD-Net, HAD-Net takes (1) the student prediction (2) teacher prediction (3) latent space features and uses a discriminator to make the inputs from teacher and students undifferentiable.


### Comments
- This method seems generalizable for any missing modality but only validated on the w/o T1CE dataset. It would be interesting to see how it performs on other missing modalities and the comparison against SOTA methods.






