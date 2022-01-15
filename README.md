# Malarial-Cell-Image-Segmentation

## Image Segmentation

- Sub-domain of computer visvion that deals with grouping similar regions or segments of an image under their respective class labels.
- Segmentation allows us to organize the data contained within images and videos into meaningful categories. 
- While image classification and object detection may tell us the presence and location of certain objects, segmentation allows us to dive deeper. It involves image feature localization in addition to just classification. 
- The model developed for image segmentation pinpoints towards a corresponding object present in the image by outlining the object's boundary. 

### 1. Features of image segmentation model

- It consists of an encoder-decoder pair instead of the single encoder present in classifiers.
  - Encoder: The encoder encodes a latent space representation of the input and is usually is a pre-trained classification network.
  - Decoder: The task of the decoder is to decode form segment maps, or in other words map outlines of each object’s location in the image.

### 2. Image segmentation tasks
**(a) Semantic Segmentation:** Semantic segmentation refers to the classification of pixels in an image into semantic classes. Pixels belonging to a particular class are simply classified to that class with no other information or context taken into consideration. 

**(b) Instance Segmentation:** An instance segmentation algorithm has no idea of the class a classified region belongs to but can segregate overlapping or very similar object regions on the basis of their boundaries. 

**(c) Panoptic segmentation:** Panoptic segmentation, the most recently developed segmentation task, can be expressed as the combination of semantic segmentation and instance segmentation where each instance of an object in the image is segregated and the object’s identity is predicted. 

### 3. Traditional image segmentation techniques
<img src="https://user-images.githubusercontent.com/67593609/149627861-bd16eb9d-839c-416f-b9fe-30bb1d18b570.png" width="400" height="350"/>

**(1) Otsu's threshold:**

**(2) Mean Shift:**

**(3) Region Growing:**

**(4) Region Split and Merge:**

**(5) Canny:** 

**(6) Gradient:**

**(7) Laplacian:**

**(8) Watershed:**

**(9) Marker Controlled Watershed:**

**(10) K-means:** 

**(11) Fuzzy C-means:** 

### 4. Image segmentation techniques using deep learning

**(1) SegNet:**

**(2) U-net:**

**(3) PSPnet:**

**(4) DeepLab:**

## About the data

### Tasks outline

## Resources
1. https://www.v7labs.com/blog/image-segmentation-guide 
2. https://www.youtube.com/playlist?list=PLZsOBAyNTZwbR08R959iCvYT3qzhxvGOE 
3. https://www.youtube.com/watch?v=J_XSd_u_Yew&list=PLZsOBAyNTZwbR08R959iCvYT3qzhxvGOE&index=8 
4. https://github.com/bnsreenu/python_for_microscopists 
5. https://www.apeer.com/home 
6. https://www.upgrad.com/blog/image-segmentation-techniques/#6_Neural_Networks_for_Segmentation 
7. https://arxiv.org/ftp/arxiv/papers/1707/1707.02051.pdf 
