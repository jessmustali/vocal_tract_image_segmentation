# Automatic Image Segmentation for Speech Production Analysis

## Overview

The purpose of this project is to develop an automatic image-segmentation method using a deep learning approach. The goal is to extract surfaces of main articulators crucial for speech production. This method can aid doctors in diagnosing and monitoring neurodegenerative diseases, as motor speech impairment may be an early observable symptom.

## Dataset

We were provided with a dataset of 820 real-time MRI images along with their respective labels. The dataset was split into 80% for training and 10% each for validation and testing. Salt and pepper noise was removed using a median filter.

## Model Architecture

The U-Net architecture, as used by Ruthven in their research, was chosen. It consists of 5 encoding layers and 5 decoding layers. Gridsearch was performed for hyperparameter optimization, exploring dropout rate, batch size, loss function, and type of pooling.

## Training and Evaluation

During training and postprocessing, the DICE coefficient was used to measure the quality of segmentation. Cross entropy was chosen as the loss function, with variations like uniform weights, adjusted weights, and custom cross entropy tested.

Results indicated that cross entropy with uniform weights performed best. The model exhibited robustness to noise, with minimal impact on results when applied to the original dataset versus denoised versions.

## Postprocessing Techniques

Various postprocessing techniques were implemented after choosing the best model. An algorithm for island detection was designed to remove isolated groups of pixels below a certain threshold. Median filters were also applied individually and in combination with island detection.

## Results

The best results were obtained by combining the median filter with the island detection algorithm, followed by raw predictions and the median filter alone. Combining multiple methods had a negative impact on the metric.

## Conclusion

In conclusion, our model demonstrated satisfactory segmentation with good visual results and mean DICE scores. It showed no overfitting and robustness to noise. Further improvements could involve exploring different loss functions and increasing the dataset size.

## Future Work

Potential future improvements include exploring additional loss functions, increasing the number of samples, and continuous refinement of postprocessing techniques.

Special thanks to [Dataset Source](https://drive.google.com/drive/folders/1kWbGhzMr72US_Iiil-zFYJ8LjL9eboor?usp=share_link) for providing the dataset used in this project.


 
