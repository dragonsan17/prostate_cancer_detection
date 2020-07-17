# Prostate cANcer graDe Assessment (PANDA) Challenge

__Kaggle Competition : https://www.kaggle.com/c/prostate-cancer-grade-assessment/overview__

__Handle : dragonsan17__

Given a dataset of slides images of prostate biopsy, we have to detect the presence of cancer by
predicting the ISUP Grade.

![GitHub Logo](/data_sample/description.PNG)

# Data Augmentations : 

* The prostate biopsy strands cover a very small area of the whole slide image. Directly using this as the
training image leads to severe underfitting, leading to a QWK score of around 65.
* Here, relevant tiles are extracted according to density of coloured pixels and combined into a single image,
so that overall size of the data decreases and also increasing the density of relevant data.
* Following shows a sample of such images after augmentations, along with the labels (ISUP Grade)

![GitHub Logo](/data_sample/sample.PNG)

# Training:

* Tried out with ResNet18, ResNet34, ResNet50, SEResNext50 and EfficientNet B0. EfficientNet B0 and Resnet34 perform
superior to others.
* Simple categorical crossentropy leads to a lower score, around QWK 80.
* Implemented Binning Loss (final later is treated as a counter rather than a classifier) along with Binary cross entropy
to achieve QWK of 85 within 10 epochs and around 87 within 40 epochs.
