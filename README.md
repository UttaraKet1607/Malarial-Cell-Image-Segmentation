# Malarial-Cell-Image-Segmentation

## Image Segmentation

- Sub-domain of computer visvion that deals with **grouping similar regions or segments of an image** under their respective class labels.
- Segmentation allows us to organize the data contained within images and videos into meaningful categories. 
- While image classification and object detection may tell us the presence and location of certain objects, segmentation allows us to dive deeper. It involves image feature localization in addition to just classification. 
- The model developed for image segmentation pinpoints towards a corresponding object present in the image by outlining the object's boundary. 

### 1. Features of image segmentation model

- It consists of an **encoder-decoder pair** instead of the single encoder present in classifiers.
  - Encoder: The encoder encodes a latent space representation of the input and is usually is a pre-trained classification network.
  - Decoder: The task of the decoder is to decode form segment maps, or in other words map outlines of each object’s location in the image.

### 2. Image segmentation tasks
**(a) Semantic Segmentation:** Semantic segmentation refers to the classification of pixels in an image into semantic classes. Pixels belonging to a particular class are simply classified to that class with no other information or context taken into consideration. 

**(b) Instance Segmentation:** An instance segmentation algorithm has no idea of the class a classified region belongs to but can segregate overlapping or very similar object regions on the basis of their boundaries. 

**(c) Panoptic segmentation:** Panoptic segmentation, the most recently developed segmentation task, can be expressed as the combination of semantic segmentation and instance segmentation where each instance of an object in the image is segregated and the object’s identity is predicted.

<img src="https://user-images.githubusercontent.com/67593609/151494147-f4e60842-d23d-4ac4-bd76-0cf9f348bb36.png" width="350" height="350" align="center"/>


### 3. Traditional image segmentation techniques
<img src="https://user-images.githubusercontent.com/67593609/149627861-bd16eb9d-839c-416f-b9fe-30bb1d18b570.png" width="400" height="350" align="center"/>

**(1) Otsu's threshold:** Otsu's binarization, takes an image with a histogram having two peaks and uses the approximate value of the middle of those peaks as the threshold value. In Otsu binarization, the threshold value from the image’s histogram can be calculated if the image is bimodal. This process is quite popular for scanning documents, recognizing patterns, and removing unnecessary colours from a file. However, this technique cannot be used for images that are not bimodal. 

**(2) Mean Shift:** This technique replaces each pixel with the mean of the pixels in a range-r neighborhood and whose value is within a distance d. It has three main input parameters: (a) a distance function for measuring distances between pixels (b) a radius (c) a value difference parameter. 

**(3) Region Growing:** Region-based segmentation algorithms divide the image into sections with similar features. This method starts with a small set of pixels and then iteratively merging more pixels according to particular similarity conditions. Region growing algorithms are used for images that have a lot of noise as the noise makes it difficult to find edges or use thresholding algorithms. 

**(4) Region Split and Merge:** A region splitting and merging algorithm focuses on performing two actions together – splitting and merging portions of the image. It first splits the image into regions that have similar attributes and merges the adjacent portions which are similar to one another. In region splitting, the algorithm considers the entire image while in region growth, the algorithm would focus on a particular point. 

**(5) Watershed:** A watershed is a transformation on a grayscale image. The watershed method converts every image into a topographical map. It considers the brightness of a pixel as its height and finds the lines that run along the top of those ridges. As basins have a lot of markers while the ridges don’t, the image gets divided into multiple regions according to the ‘height’ of every pixel. It has many applications in the medical sector such as MRI, medical imaging, etc.

**(6) K-means:** It utilizes k-means algorithm to classify an image through a specific number of clusters. It starts the process by dividing the image space into k pixels that represent k group centroids. Then it assigns each object to the group based on the distance between them and the centroid. When the algorithm has assigned all pixels to all the clusters, it can move and reassign the centroids. After a point, when the centroids no more change, the final clusters are formed. 

**(7) Fuzzy C-means:** Fuzzy C-means (FCM) is a method of clustering which allows one piece of data to belong to two or more clusters. Fuzzy logic is a multi-valued logic derived from fuzzy set theory. However, the drawback of FCM is that it is sensitive to image noise. FCM is popularly used for soft segmentations like brain tissue model

### 4. Image segmentation techniques using deep learning

**(1) DeconvNet:** In this DeconvNet, the output label map is obtained by gradual deconvolution and unpooling. It works in three main steps:
- **Unpooling:** The DeconvNet places the reconstructions from the layer above into appropriate locations based on the maxima found to obtain an unpooled map.
- **Rectification:** ConvNet uses ReLU non-linearity to rectify the feature maps. To obtain valid feature reconstructions at each layer, the reconstructed signal is thus also passed through a ReLU non-linearity.
- **Filtering:** ConvNet uses learned filters to convolve the feature maps to a lower dimension. The DeConvNet uses the transpose of this learned filter to the rectified representation from the step above to reconstruct the deconvolved layer output. 

<img src="https://user-images.githubusercontent.com/67593609/151492428-f11e4cd5-b7ea-45ee-af8f-731500a6f98c.png" width="600" height="170" align="center"/>

**(2) U-net:** The architecture contains two paths. 
- **Encoder:** First path is the contraction path which is used to capture the context in the image. The encoder is just a traditional stack of convolutional and max pooling layers. 
- **Decoder:** The second path is the symmetric expanding path which is used to enable precise localization using transposed convolutions. 
Thus it is an end-to-end fully convolutional network so, it only contains Convolutional layers and does not contain any Dense layer because of which it can accept image of any size.

<img src="https://user-images.githubusercontent.com/67593609/151492919-1013774a-8770-4b76-a778-f49f7a534d61.png" width="450" height="320" align="center"/>

**(3) SegNet:** 

- **Encoder:** At the encoder, convolutions and max pooling are performed. There are 13 convolutional layers from VGG-16. (The original fully connected layers are discarded.) While doing 2×2 max pooling, the corresponding max pooling indices (locations) are stored.
- **Decoder:** At the decoder, upsampling and convolutions are performed. At the end, there is softmax classifier for each pixel. During upsampling, the max pooling indices at the corresponding encoder layer are recalled to upsample as shown above. Finally, a K-class softmax classifier is used to predict the class for each pixel.

<img src="https://user-images.githubusercontent.com/67593609/151491400-4e9f7b56-0df5-4931-8baf-7cdc9fe61eba.png" width="600" height="170" align="center"/>

## About the data
The data is a repository of segmented cells from the thin blood smear slide images from the Malaria Screener research activity. This data is a result of images taken by a mobile application that runs on a standard Android smartphone attached to a conventional light microscope which was developed by researchers at the Lister Hill National Center for Biomedical Communications (LHNCBC), part of National Library of Medicine (NLM).

The dataset contains 2 folders
- Infected
- Uninfected
- 
And a total of 27,558 images.

The main aim behind the generation of this data was to reduce the burden for microscopists in resource-constrained regions and improve diagnostic accuracy. The images were manually annotated by an expert slide reader at the Mahidol-Oxford Tropical Medicine Research Unit in Bangkok, Thailand. The de-identified images and annotations are archived at NLM. 

(Source: https://lhncbc.nlm.nih.gov/LHC-downloads/downloads.html#malaria-datasets)

### Tasks outline

<img src="https://user-images.githubusercontent.com/67593609/151516069-db326736-d8ad-44eb-beff-648e1acdca3c.png" width="800" height="350"  align="center"/>

## Resources
1. https://www.v7labs.com/blog/image-segmentation-guide 
2. https://www.youtube.com/playlist?list=PLZsOBAyNTZwbR08R959iCvYT3qzhxvGOE 
3. https://www.youtube.com/watch?v=J_XSd_u_Yew&list=PLZsOBAyNTZwbR08R959iCvYT3qzhxvGOE&index=8 
4. https://github.com/bnsreenu/python_for_microscopists 
5. https://www.apeer.com/home 
6. https://www.upgrad.com/blog/image-segmentation-techniques/#6_Neural_Networks_for_Segmentation 
7. https://arxiv.org/ftp/arxiv/papers/1707/1707.02051.pdf 
8. https://arxiv.org/pdf/1902.09063.pdf
9. https://www.youtube.com/watch?v=UYmVL1ZXp_w 
