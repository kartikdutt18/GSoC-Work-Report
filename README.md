<p align="center">
  <img width="556" height="112" src="https://github.com/kartikdutt18/GSoC-Work-Report/blob/master/src/logo.png">
</p>

#### Organisation: [mlpack](https://github.com/mlpack)

#### Project: Application of ANN Algorithms implemented in mlpack

#### Mentor: [Sangyeon Kim](https://github.com/KimSangYeon-DGU) and [Saksham Bansal](https://github.com/saksham189)

## Abstract
This year my proposal was selected for `Application of ANN Algorithms implemented in mlpack` as part of Google Summer of Code, 2020.`mlpack` is an intuitive, fast and flexible `C++` machine learning library with bindings to other languages. Over the course of the last couple of years, Computer Vision has played a crucial role in the field of Deep Learning. Object detection is one of the most prominent problem in computer vision and algorithms such as YOLOv3 and tiny-YOLOv3 play a very important role in tackling them.

## Goal
The goal of this proposal was to implement `restructure the models repository`, implement `dataloaders`,
add `metrics / utility functions for object detection`, add `DarkNet 19 / 53` models as well as implement `YOLOv1` and `YOLOv3 (tiny / full)`.

During the course of the project, some blockers were encountered such as very long training time for models and missing implementation of BatchNorm (2d). These goals were also added to the project.

## Results
We met most of those initially proposed as well as some additional targets that were necessary for pursuing the project goals. The models repository was restructured, dataloaders were implemented, metrics and utility functions for object detection were added, DarkNet models were added, YOLOv1 implementation was completed as well as forward propogation for YOLOv3 (tiny / full) was completed and mlpack-PyTorch weight translator was also created and some bug fixes were made. For more details, refer to the contributions sections which describes aim and status of each contribution.

## Contributions
Contributions were made to the [mlpack/mlpack](https://github.com/mlpack/mlpack), [mlpack/models](https://github.com/mlpack/models), [mlpack/examples](https://github.com/mlpack/examples) and [kartikdutt18/mlpack-PyTorch-Weight-Translator](https://github.com/kartikdutt18/mlpack-PyTorch-Weight-Translator).

For simplicity, I have divided contributions made into the repository they were made to.

## mlpack/mlpack Contributions

<p align="center">
  <img width="350" height="250" src="https://github.com/kartikdutt18/GSoC-Work-Report/blob/master/src/mlpack_repo_contributions.png">
</p>

### 1. [Add IoU metric for bounding boxes](https://github.com/mlpack/mlpack/pull/2402)

#### Aim:
1. Add IoU metric for bounding boxes.
2. Add tests for IoU metric.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.

### 2. [Add Non Maximal Supression for bounding boxes](https://github.com/mlpack/mlpack/pull/2410)

#### Aim:
1. Add Fast Non Maximal Suppression.
2. Add tests for this metric.
3. Verify values using torch.ops.nms()

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.

### 3. [Bug Fix : Check correctness of shape in Transposed Conv. layer only when output width and height aren't zero](https://github.com/mlpack/mlpack/pull/2436)

#### Aim:
1. Transposed convolution should check for correctness only when output width / height is specified.
2. Add simple test to show that a model can be declared without specifying width and height.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.

### 4. [Extending Support of BatchNorm layer to Convolutional Layer output](https://github.com/mlpack/mlpack/pull/2474)

#### Aim:
1. Implement mini-BatchNorm (BatchNorm2D) to support multi-channel output (such as output from Conv. layer).
2. Implement Backward propogation for the same.
3. Ensure parameters match and verify output from PyTorch.
4. Add tests for the same.
5. Verify output of a small model with and without BatchNorm2D.
6. See speed increase with BatchNorm2D compared to previous implementation of BatchNorm.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.

### 5. [Optimize Backward Propogation for BatchNorm Layer](https://github.com/mlpack/mlpack/pull/2512)

#### Aim:
1. In this PR, an alternative implementation to backward propogation of BatchNorm which performs faster in Python.
2. Add tests to verify output.

#### Status :
The implementation is complete. However, the gradient test fails with this implementation. Since, this is an optimization and doesn't change API of the layer, it was decided to leave it as it is for now.

### 6. [Changes in Deterministic settings of FNN](https://github.com/mlpack/mlpack/pull/2552)

#### Aim:
1. This was a PR for bug fix. The FFN class didn't set deterministic parameter for layers correctly.
2. This PR fixed the afforementioned problem and set layers in deterministic mode for prediction and training mode during training.
3. Verified its working.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.

Speed Improvement | Model Performance Improvement |
:-------------------------:|:-------------------------:|
<img src="https://github.com/kartikdutt18/GSoC-Work-Report/blob/master/src/BatchNormSpeedComparision.png" width="420" height="320"> | <img src="https://github.com/kartikdutt18/GSoC-Work-Report/blob/master/src/BatchNormCNN.png" width="520" height="320"> |


## mlpack/models Contributions
<p align="center">
  <img width="350" height="250" src="https://github.com/kartikdutt18/GSoC-Work-Report/blob/master/src/models_repo_contributions.png">
</p>

### 1. [Restructuring - 1 (Adding Data loader and associated Utility Functions)](https://github.com/mlpack/models/pull/3)

#### Aim:
1. Set basic structure for models repository.
2. Add CSV Dataloader.
3. Add unit testing for models repository using BOOST_TESTS.
4. Add testing in Azure pipelines.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.

### 2. [Adding Documentation for DataLoader](https://github.com/mlpack/models/pull/9)

#### Aim:
1. Add documentation for dataloader.
2. Add wiki tutorial for dataloader and utility functions.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase

### 3. [Restructuring 2 - Add Utility functions and Run all Tests](https://github.com/mlpack/models/pull/12)

#### Aim:
1. Add Utility functions for the models repository.
2. Add tests and run all tests in azure.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.


### 4. [Image Dataloader with Field type](https://github.com/mlpack/models/pull/18)

#### Aim:
1. Implement `Augmentation` class to resize images.
2. Add Object Detection DataLoader to load Pascal VOC dataset.
3. Add Object Classification DataLoader to load image dataset and assign labels.
4. Add tests for Object Detection DataLoader, Object Classification DataLoader and Augmentation class.
5. Add support for CIFAR-10 dataset.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.

### 5. [Image Dataloader Documentation](https://github.com/mlpack/models/pull/19)

#### Aim:
1. Add documentation for image dataloader.
2. Add wiki tutorial for image dataloader.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.


### 6. [Add DarkNet models, Ensmallen Callbacks and ChannelFirst Preprocessor](https://github.com/mlpack/models/pull/20)

#### Aim:
1. Implement DarkNet model such that we can reproduce PyTorch models in mlpack.
2. Use mlpack-weight Converter to translate weights into the mlpack models as well as verify the model output. This became necessary since training the model took a very long time.
3. Add Channel-First PreProcessor function that converts an image loaded in mlpack to the matrix as if it was loaded in PyTorch i.e. transpose the channels, convert numbers to uint8 and divide them by 255.
4. Add Periodic Save Callback that allows periodic saving of models during training.
5. Add Print Metric Callback that allows printing any metric implemented in mlpack after each epoch on either training set, validation set or both.
6. Add tests for DarkNet class.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.

### 7. [DarkNet Documentation](https://github.com/mlpack/models/pull/23)

#### Aim:
1. Add documentation for DarkNet.
2. Add wiki tutorial for DarkNet and ensmallen callbacks.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.

### 8. [Remove simpler models](https://github.com/mlpack/models/pull/28)

#### Aim:
1. To nearly complete restructuring, all simple models were removed from models repository.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.

### 9. [YOLO PreProcessor](https://github.com/mlpack/models/pull/25)

#### Aim:
1. This PR converts annotations / bounding boxes loaded using DataLoader to encoded feature maps.
2. This supports all YOLO versions between 1 and 3.
3. Add tests to verify output of the PreProcessor from PyTorch implementation of models.


#### Status :
Complete. This PR is ready to merge. It was decided that all YOLO related PRs will be merged with the YOLO model.

### 10. [YOLO Loss Function / Detector](https://github.com/mlpack/models/pull/29)

#### Aim:
1. Add Loss function to decode output from YOLO model so that the model can be trained.
2. Add detailed tests to verify loss functions.

#### Status :
Complete. This PR is ready to merge. It was decided that all YOLO related PRs will be merged with the YOLO model.

### 11. [Add YOLO class](https://github.com/mlpack/models/pull/24)

#### Aim:
1. Implement YOLOv1 model.
2. Add tests to verify it's working.

#### Status :
Complete. The model implementation is complete. The only thing left is to verify the model output using mlpack-PyTorch-weight-converter. Once the output is verfied this PR can be merged.

### 12. [Bounding Box Visualizer](https://github.com/mlpack/models/pull/31)

#### Aim:
1. Add function to plot and save bounding boxes on an image.

#### Status :
The core implementation is complete. Once the review suggestions are incorporated, this PR can be merged as well.

### 13. [Add YOLOv3 Layer](https://github.com/mlpack/models/pull/32)

#### Aim:
1. Add YOLOv3 layer i.e. This layer allows skip connections which are later upscaled and concatenated.
2. With this we can implement YOLOv3 tiny / full in one go.
3. Since the we already have DarkNet 53 blocks for YOLOv3, we can simply pass it in this class to obtain YOLOv3 model.

#### Status :
The forward propogation is complete. The next steps include writing the backward propogation and verifying it's output.

## mlpack/examples Contributions

### 1. [Add BatchNorm to CNN example](https://github.com/mlpack/examples/pull/106)

#### Aim:
1. Add BatchNorm layer to CNN example in examples repository.
2. See if there is any performance improvement.

#### Status :
Complete. Everything in the PR has been completed and is ready for merging.

## kartikdutt18/mlpack-PyTorch-Weight-Translator Contributions
<p align="center">
  <img width="350" height="250" src="https://github.com/kartikdutt18/GSoC-Work-Report/blob/master/src/mlpack-PyTorch-Translator.png">
</p>

### 1. [mlpack-PyTorch-Weight-Translator](https://github.com/kartikdutt18/mlpack-PyTorch-Weight-Translator)

#### Aim:
1. Generate CSV files for weights, biases and all trainable parameters from PyTorch models.
2. Generate XML file for PyTorch model that holds the structure as well as files necessary to reproduce the model.
3. Create a parser in C++ which loads all weights and biases from XML file to the mlpack model.
4. Test it on DarkNet 19 and DarkNet 53 model.
5. Verify output for each layer and add tests for layers that were missing tests. [Add tests for Conv. Layer](https://github.com/mlpack/mlpack/pull/2548).
6. Create sample notebooks to see if models match in mlpack and PyTorch.
7. Create bash file to test the models.
8. Match the accuracies of the models and save the models weights.

#### Status :
Complete. Since, this was a different repository, I have created a bash file for testing.



## Other Contributions
#### 1. [Use 0 to numClass Labels instead of 1 to 10 where NLL is used](https://github.com/mlpack/examples/pull/104)
#### 2. [Move Layer to Sequential Type](https://github.com/mlpack/mlpack/pull/2519)
#### 3. [Style fixes in mlpack-repo](https://github.com/mlpack/mlpack/pull/2491/files)
#### 4. [Document CMake Flags](https://github.com/mlpack/mlpack/pull/2475)
#### 5. [Documentation fix in BatchNorm](https://github.com/mlpack/mlpack/pull/2453)
#### 6. [Remove Python 2.7 from Azure builds](https://github.com/mlpack/mlpack/pull/2430)

## Blog
You can follow my weekly progress on my medium blogs.
[Medium Articles by kartikdutt18](https://medium.com/@kartikdutt18)

## Scope and Future Work
I would like to continue contributing to mlpack's repositories since it alligns well with my personal area of interest as well. Firstly, I would like to finish testing my currently open PRs and have them merged into the codebase. Secondly, during the project we got to see YOLOv4 and YOLOv5 research papers being published hence it would be nice to spend some implementing these models as well. I would also like to get more people interested in mlpack/models repository mantaining same or higher standard as above.

## Acknowledgement
On a final note, I am extremely grateful to my mentors, Sangyeon Kim and Saksham Bansal for all their support, reviews and help. I am also very thankful for their patience whenever I got stuck and their suggestions that helped me in resolving them.

I am also thankful to mlpack community for all their reviews help and suggestions. I am also thankful to Marcus, Ryan Curtin and Ryan Birmingham that helped me in contributing to mlpack.

mlpack was the first Machine Learning library that I contributed to, and it has been a really amazing journey. I also learned a lot through this project and I intend to continue contributing to mlpack.

I am also thankful to Google for the opportunity to work on this wonderful project, which helped me learn a lot in such a short period of time.
