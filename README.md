# Style Transfer

We recreate a style transfer method that is outlined in the paper, [Image Style Transfer Using Convolutional Neural Networks, by Gatys](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Gatys_Image_Style_Transfer_CVPR_2016_paper.pdf) in PyTorch.

In this paper, style transfer uses the features found in the 19-layer VGG Network, which is comprised of a series of convolutional and pooling layers, and a few fully-connected layers. In the image below, the convolutional layers are named by stack and their order in the stack. Conv1_1 is the first convolutional layer that an image is passed through, in the first stack. Conv2_1 is the first convolutional layer in the *second* stack. The deepest convolutional layer in the network is conv5_4.

<img src='https://ppt.cc/fIGJGx@.png' width=80% />

### Separating Style and Content

Style transfer relies on separating the content and style of an image. Given one content image and one style image, we aim to create a new, _target_ image which should contain our desired content and style components:
* objects and their arrangement are similar to that of the **content image**
* style, colors, and textures are similar to that of the **style image**

An example is shown below, where the content image is of a cat, and the style image is of [Hokusai's Great Wave](https://en.wikipedia.org/wiki/The_Great_Wave_off_Kanagawa). The generated target image still contains the cat but is stylized with the waves, blue and beige colors, and block print textures of the style image!

<img src='https://ppt.cc/f0sV3x@.png' width=80% />

According to the paper, we extract feature maps after layer conv4_2 for content information. We calculate gram matrixes after layer conv1_1, conv2_1, conv3_1 and conv4_1 for style information.

### Input
This method can take any images as input. We use the two pictures below for content image and style image.
<img src='https://i.imgur.com/mqwfKBL.png' width=80% />

### Result
We trained for 2000 epoches with Adam optimizer(lr=0.003).The result images after every 400 epoches is shown below:

<img src='https://ppt.cc/fvZskx@.png' width=100% />
