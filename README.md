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


mlpack/mlpack Contributions |  mlpack/models Contributions |  kartikdutt18/mlpack-PyTorch-Weight-Translator Contributions
:-------------------------:|:-------------------------:|:-------------------------:
![](https://github.com/kartikdutt18/GSoC-Work-Report/blob/master/src/mlpack_repo_contributions.png)  |  ![](https://github.com/kartikdutt18/GSoC-Work-Report/blob/master/src/models_repo_contributions.png) | ![](https://github.com/kartikdutt18/GSoC-Work-Report/blob/master/src/mlpack-PyTorch-Translator.png)

### 1. [Restructuring - 1 (Adding Data loader and associated Utility Functions)](https://github.com/mlpack/models/pull/3)

#### Aim:
1. Set basic structure for models repository.
2. Add CSV Dataloader.
3. Add unit testing for models repository using BOOST_TESTS.
4. Add testing in Azure pipelines.

#### Status :
Merged. Everything in the PR has been completed and merged into the codebase.

