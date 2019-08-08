# Projects
## Tiny_Imagenet_54_8-val_acc.ipynb
Custom deep-learning architecture achieving **54.8% top-1** validation accuracy on **Tiny imagenet dataset** (32x32 images, 200 classes), executed on **Google Colab** while limiting the **13.4 million total parameters**. Key features of the model -
* keras framework used
* Use of depthwise separable convolutions along with normal ones 
* Maximum number of channels used is 2048, to abide by the limited available hardware in Google Colab
* Receptive Field of the network is 64x64, even though the image size is 32x32 for making the network to understand the entire object (not image) size
* Image Augmentations - Horizontal flip, Gaussian Blur, Multiply, CoarseDropout (similar to Cutout), Affine transformations - from imgaug open-source library
* Input image resized between sizes- 16x16, 32x32, 64x64 - for making the network learn objects of small sizes
* Callbacks - ReduceLROnPlateau, CyclicLR, ModelCheckpoint
* One-cycle policy used for varying learning rates, with the max and base learning rates taken from LR Finder
* For most misclassified classes in training dataset, network fed more of the images from these classes to help learn the classes.
* Misclassified classes from validation dataset are found and the class weights in loss function changed to penalize mistakes in identifying these classes. 
