# Diabetic-Retinopathy-Classification

Diabetic retinopathy is a progressive and potentially sight-threatening complication of diabetes mellitus. It occurs when high levels of blood sugar damage the blood vessels in the retina, the light-sensitive tissue at the back of the eye. As the condition advances, these blood vessels can leak or become blocked, leading to impaired vision and, in severe cases, blindness. One of the challenging aspects of diabetic retinopathy is that it often develops without noticeable symptoms in its early stages, making regular eye screenings crucial for early detection and intervention. The risk of developing diabetic retinopathy increases with the duration of diabetes, emphasizing the importance of ongoing monitoring for individuals with diabetes to prevent irreversible vision loss.

Early detection of diabetic retinopathy is of paramount importance for effective management and intervention. Regular eye examinations, including retinal imaging, enable healthcare professionals to identify signs of diabetic retinopathy in its early stages when treatment options are more effective. Timely intervention, such as laser therapy or intraocular injections, can help manage the condition and prevent or slow down vision impairment. Given the rising prevalence of diabetes worldwide, addressing diabetic retinopathy through proactive screening and timely medical intervention is crucial to preserving the vision and overall quality of life for individuals living with diabetes.

## Dataset
The dataset consists of retina scan images used for detecting diabetic retinopathy, and it is derived from the APTOS 2019 Blindness Detection dataset. To facilitate compatibility with various pre-trained deep learning models, the original images have been resized to 224x224 pixels. The dataset is organized into five folders, each corresponding to a specific severity or stage of diabetic retinopathy, as outlined in the provided train.csv file:

1. No_DR (Class 0): This category includes images where no signs of diabetic retinopathy are observed. The retina scans in this class are considered normal without any indication of the condition.

2. Mild (Class 1): Images in this class depict early-stage diabetic retinopathy with mild signs of the condition. Although there are indications of abnormalities, they are not yet severe.

3. Moderate (Class 2): Retina scans in this class show a moderate level of diabetic retinopathy. The signs of the condition are more pronounced compared to the mild stage but have not reached a severe level.

4. Severe (Class 3): This category contains images with severe diabetic retinopathy. The condition has progressed significantly, and there are notable signs of damage to the retina.

5. Proliferate_DR (Class 4): Images in this class represent the proliferative stage of diabetic retinopathy, which is the most advanced and severe stage. Proliferative diabetic retinopathy involves the growth of abnormal blood vessels, posing a serious threat to vision.

Dataset can be found at https://www.kaggle.com/datasets/sovitrath/diabetic-retinopathy-224x224-2019-data 

## Preprocessing 

The images obtained undergo thorough preprocessing to enhance their quality for effective model learning. A crucial step involves normalization, wherein pixel values are rescaled to a range between 0 and 1, ensuring uniform input for subsequent deep learning model training. Moreover, contrast enhancement techniques, such as Contrast Limited Adaptive Histogram Equalization (CLAHE) and histogram matching, are employed to enhance the visibility of relevant features in the images. Subsequently, gamma correction is applied, followed by sharpening and closing operations on the output. The final step involves thresholding to extract distinctive features of the eye. These preprocessing methods are implemented to enhance the model's robustness and promote better generalization.

1. SMOTE (Synthetic Minority Over-sampling Technique): SMOTE is a technique used to address class imbalance in datasets. It generates synthetic samples for the minority class by interpolating between existing minority class instances. In the context of diabetic retinopathy classification, SMOTE may be applied to ensure that the model is exposed to a balanced representation of different severity levels of the disease.
CLAHE (Contrast Limited Adaptive Histogram Equalization):

2. CLAHE is a contrast enhancement technique applied to images. It divides the image into small, overlapping tiles and enhances the contrast in each tile independently. This method is effective in bringing out finer details and improving the visibility of subtle features in retinal images.
Histogram Matching:

3. Histogram matching is a technique used to adjust the intensity distribution of an image to match a specified reference distribution. In the context of diabetic retinopathy classification, it can be employed to standardize the intensity characteristics of images, ensuring consistency and improving the model's ability to discern relevant features.
Gamma Correction:

4. Gamma correction is a non-linear operation that adjusts the brightness and contrast of an image by modifying the intensity values. It is often applied to correct for variations in illumination across images, ensuring that the model is not influenced by inconsistent lighting conditions during training.
Sharpening:

5. Sharpening is an image processing technique that enhances the edges and fine details in an image. In the context of diabetic retinopathy classification, sharpening can help bring out subtle structures in the retinal images, aiding the model in capturing important diagnostic features.
Closing:

6. Closing is a morphological operation that involves the dilation followed by erosion of an image. It is used to fill small gaps, smooth contours, and eliminate small protrusions. In the context of image preprocessing for diabetic retinopathy, closing can help in refining the overall structure of the retinal features.
Thresholding:

7. Thresholding involves setting a threshold value to segment an image into distinct regions. In the context of diabetic retinopathy classification, thresholding can be used to extract specific features of interest, such as the boundaries of lesions or abnormalities in retinal images, aiding in subsequent analysis and feature extraction.

## Models Used
1. Convolutional Neural Networks (CNN): CNNs are deep neural networks designed for grid-structured data like images. They employ convolutional layers to automatically learn hierarchical feature representations. Convolutional operations enable the network to capture local patterns, while pooling layers downsample spatial dimensions. This architecture is adept at automatically extracting features such as edges and textures crucial for image classification.
VGG16:

2. VGG16: Part of the VGG architecture, is notable for its depth, featuring 16 layers. It utilizes small convolutional filters (3x3) in a stacked configuration, enabling effective feature learning. The simplicity and effectiveness of VGG16, especially in image classification, have made it a benchmark architecture. Though surpassed by newer models, VGG16 remains influential for its structural clarity.
U-Net:

3. U-Net: U-Net is tailored for semantic segmentation tasks. Its distinctive U-shaped architecture combines contracting and expansive paths. The contracting path captures context through convolution and pooling, while the expansive path enables precise localization through transposed convolutions. U-Net is widely used in medical image segmentation and related applications due to its ability to preserve spatial information.
VGGNet:

4. VGGNet: VGGNet refers to the VGG architecture family. While VGG16 is one variant, others like VGG19 also exist. Characterized by uniform architectures with small convolutional filters, VGGNets are known for their simplicity. They played a pivotal role in demonstrating the significance of depth in neural networks. VGGNets are foundational for understanding the trade-offs in network architecture.
