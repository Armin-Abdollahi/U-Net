# U-Net

Network structure
U-Net is a convolutional neural network architecture commonly used for image segmentation tasks. It was first introduced in a paper entitled "U-Net: Convolutional Networks for Biomedical Image Segmentation" by Ronneberger. U-Net architecture is based on fully convolutional network (FCN) and consists of two parts: contracting path and expansive path.

The contracting path is responsible for capturing the background of the input image and consists of a series of convolution layers and max-pooling layers. Convolution layers are used to extract features from the input image, while max-pooling layers are used to downsample the feature maps and reduce the spatial dimensions of the input image.

The expansive path is responsible for producing the final segmentation map and consists of a series of upsampling layers and convolution layers. Upsampling layers are used to increase the spatial dimensions of feature maps, while convolution layers are used to refine the segmentation map.

The U-Net architecture also includes jump connections that connect the respective layers in the contracting and expansive paths. These jump connections allow the network to use high-resolution feature maps from the contracting path to produce more accurate feature maps in the expansive path.

Regarding the pre-trained U-Net network, there are several variants of the U-Net architecture that are pre-trained on different datasets. One of these changes is the U^2-Net architecture, which was introduced by Qin in a paper entitled "U^2-Net: Going Deeper with Nested U-Structure for Salient Object Detection". The U^2-Net architecture is based on the U-Net architecture and consists of a series of nested U structures that allow the network to capture more complex features in the input image. The U^2-Net architecture is pre-trained on the DUTS dataset and achieves improved performance on several salient object detection benchmarks.









UNet architecture
Unet netowrk model has 3 parts:

1. Contracting/Downsampling path.
2. Bottleneck Block
3. Expansive/Upsampling path.


Contracting path:
It consists of two x33 unpadded convolutions, each consisting of a rectified linear unit (ReLU) and a 2x2 max pooling with a stride of 2 for downsampling. After each downsampling operation, the number of feature channels is doubled.

Bottleneck Block:
Bottleneck block connects the contracting and expansive paths. This block performs two layerless convolutions each with 1024 filters and prepares for the expansive path.

Expansive path:
Each step in the expansive path consists of an upsampling of the feature map, followed by a x22 convolution ("up-convolution") using shifted convolutions, a concatenation with the corresponding feature map from the contracting path, and two 3x3 convolutions, which Each is looking for a ReLU. Shifted convolution is a sampling method to increase the size of images.

Skip Connections:
Skip connections from the contracting path are joined with the corresponding feature maps in the expansive path. These jump junctions provide higher resolution features for better localization and learning representations from the input image. They also help recover any location information that may have been lost during sampling

Final layer:
In the final layer, a x11 convolution is used to map each (64 component) feature vector to the desired number of classes.

The whole network consists of 23 convolution layers.
