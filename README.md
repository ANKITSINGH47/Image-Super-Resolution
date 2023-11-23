# Image-Super-Resolution
Abstract— Image Super Resolution refers to enhancing a
low-quality image to a high-quality image. It is very
important for applications such as Surveillance, Medical
Treatment, Media. Lots of development has been made in
recent years in this area with the help of Machine learning
methods. In this paper, we try to implement Single-Image
Super Resolution using SRCNN on BSD300, BSD100
CIFAR-10 datasets. We have provided the model with
images in different formats such as blurred, /2 down
sampled and /4 down sampled. Further we have compared
the outputs to find out what method can yield a better
result.

<br>

## I.INTRODUCTION
Image Super Resolution in one of the most common image
restoration issue that has been getting attention over the years.
The purpose of Image Super-Resolution (ISR) is to generate a
higher resolution image from lower resolution images i.e.,
recover information lost during processing or not available. High
resolution image has high pixel density & thereby provide more
information about the original scene. The need for high
resolution is common in computer vision applications for better
performance in pattern recognition and analysis of images. High
resolution is also of importance in medical imaging for
diagnosis. Many applications require zooming of a specific area
of interest in the image wherein high resolution becomes
essential, e.g., surveillance, forensic and satellite imaging
applications. However, high resolution images are not always
available. This is since the setup for high resolution imaging
proves expensive and also it may not always be feasible due to
the inherent limitations of the sensor, optics manufacturing
technology. These problems can be overcome through the use of
image processing algorithms, which are relatively inexpensive,
giving rise to concept of super-resolution. It provides an
advantage as it may cost less and the existing low resolution
imaging systems can still be utilized Here, we have used the
CIFAR-10,BSD300, BSD100 datasets for training our model.
The CIFAR-10 dataset consists of 60000 32x32 color images in
10 classes, with 6000 images per class. There are 5000 training
images. We tested our model with SET5 dataset. The training
batches contain the images in random order, but some training
batches may contain more images from one class than another.
Between them, the training batches contain exactly 5000 images
from each class and BSD300 dataset on another type of model
with a blurring the input and BSD100 dataset on other model
with a scale factor of 2. These modules, our proposed model is
efficient at separating the noise and texture of the single image.

<br>

## II. BACKGROUND AND PRIOR WORK
Single Image Super-Resolution: Super-resolution is based on
the idea that a combination of low resolution (noisy) sequence
of images of a scene can be used to generate a high-resolution
image or image sequence. Thus, it attempts to reconstruct the
original scene image with high resolution given a set of
observed images at lower resolution. The general approach
considers the low-resolution images as resulting from
resampling of a high-resolution image. The goal is then to
recover the high-resolution image which when resampled based
on the input images and the imaging model, will produce the
low resolution observed images. Thus, the accuracy of imaging
model is vital for super-resolution and an incorrect modeling,
say of motion, can actually degrade the image further. The
observed images could be taken from one or multiple cameras
or could be frames of a video sequence. These images need to
be mapped to a common reference frame. This process is
registration. The super-resolution procedure can then be applied
to a region of interest in the aligned composite image. The key
to successful super-resolution consists of accurate alignment
i.e., registration and formulation of an appropriate forward
image model. The figure 1 below shows the stages in superresolution process

![Screenshot from 2023-11-23 15-50-55](https://github.com/ANKITSINGH47/Image-Super-Resolution/assets/47277960/5c2cec11-2d2c-4fc7-b292-1d8f285dda97)


## III. DATA AND METHODOLOGY
We started with studying the methods used by various sources,
and started our work by importing the relevant models.
We downloaded the CIFAR-10, BSD300, BSD100 datasets as
it contains lots of images for training the model. We used
different datasets on three different models and tested our
model with SET5 dataset.
For Training the Model, we tried 3 different approaches
1. Linear Down-Sampling: In order to obtain low resolution
image, here we down-sampled the images by 4
2. Bicubic Down-Sampling: we down-sampled images by 2
3. Blurred Image: We blurred the image using gaussian
kernel of window size=13.
The images were now basically divided into 2, the original
image which could be provided as Target to the Model and the
degraded image as the Input to the Model. We used sequential
layer of 2D convolution as our model, with internal nodes
having ReLu and the final node having Linear activation. We
then compiled the model with Adam Optimizer, selected the
Type of Loss as Mean Square Error. We ran the model with
different batch sizes and for different count of epochs and found
that the accuracy increased for with the increase in number of
Epochs.

## IV. EXPERIMENTS AND RESULTS
![Screenshot from 2023-11-23 15-51-49](https://github.com/ANKITSINGH47/Image-Super-Resolution/assets/47277960/9a6ad1bb-cf70-46d3-8052-f86c6b330e60)


![Screenshot from 2023-11-23 15-52-07](https://github.com/ANKITSINGH47/Image-Super-Resolution/assets/47277960/41ac2629-9de2-4565-9903-4b7f88e62e17)



On, subjecting our model with different type of input we
found that our model worked better on down-sampled by 4
images refer (A), with accuracy of approx. 0.89. Even though
we were able to achieve accuracy close to 0.87 using Blurred
images the subjective quality of the images was not at par with
Linear input and finally for down-sampled images we were
able to achieve accuracy close to 0.73 but the subjective
quality was much better than expected.


## V. CONCLUSION AND FUTURE WORK
In this paper, we propose a model to solve the image super
resolution that is robust to noisy and LR image. We present a
architecture with parallel modules to handle the noise and
texture effectively at the same time. In future work we hope
that the use of our framework will solve a variety of image
restore operations. In the real world, multiple degradation
factors occur arbitrarily. Therefore, we also plan to investigate
to solve the various unknown degradation with the single
model. This is one of the ultimate issues to be solved urgently
in image processing.
