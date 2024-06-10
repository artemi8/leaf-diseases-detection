# Leaf Disease Detection using YOLOv8

## Introduction

Leaf diseases pose significant threats to agricultural productivity and food security. This project aims to identify various leaf diseases using an object detection approach with the YOLOv8n model.

## Dataset

The dataset was sourced from [Roboflow Universe](https://universe.roboflow.com/artificial-intelligence-82oex/detecting-diseases), containing images labeled with multiple leaf diseases. The dataset was pre-split into training and validation sets.

## Model Overview

We utilized the YOLOv8n model, a state-of-the-art object detection model with approximately 3.2 million parameters. Initially, YOLOv9 was considered, but due to training bugs, we switched to YOLOv8n.

## Implementation Steps

1. **Data Preparation**:
   - Data augmentation was performed using YOLOv8's default settings, including mosaic augmentation, random scaling, and color jittering.

2. **Model Training**:
   - **First Experiment**: Trained for 70 epochs without class weights.
   - **Second Experiment**: Trained for 100 epochs with class weights based on class imbalance.

3. **Evaluation**:
   - Model performance was evaluated using precision, recall, mAP@50, and mAP@50-95.
   - Example images with ground truth and predicted bounding boxes were generated.

## Results

![Training Curves](runs/detect/train_2/results.png)
![Precision-Recall Curves](runs/detect/train_2/PR_curve.png)

- **First Experiment**:
  - mAP@50: 0.917
  - mAP@50-95: 0.78
- **Second Experiment**:
  - mAP@50: 0.923
  - mAP@50-95: 0.79

The second experiment, which incorporated class weights and extended training, resulted in improved mAP@50 and mAP@50-95 scores. While the improvements (from 0.917 to 0.923 for mAP@50 and from 0.78 to 0.79 for mAP@50-95) may appear small, they are significant in the context of object detection, indicating better overall model reliability and robustness. Notably, the second experiment showed better predictions for classes with fewer instances, such as Strawberry Blossom Blight, where experiment 1 had more false positives, this can be seen below in the example predictions comparison of experiment 1 versus experiment 2.

## Example Predictions

**Experiment 1:**
![Predicted Image vs Ground Truth Image](runs_predictions/exp_1/1.png)

**Experiment 2:**
![Predicted Image vs Ground Truth Image](runs_predictions/exp_2/4.png)

## Acknowledgments

We acknowledge the use of the YOLOv8 model and the dataset from [Roboflow Universe](https://universe.roboflow.com/).
