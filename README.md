# IMO-Dangerous-Goods-Sticker-Detection
Detecting **IMO/Dangerous Goods** stickers on shipping containers is crucial for safety, compliance, and operational efficiency. This project aims to identify 20 different classes of hazardous material stickers on shipping containers

## Table of Contents
1. [Overview](#overview)  
2. [Dataset & Challenges](#dataset--challenges)  
   - [Rare Classes & Augmentation](#rare-classes--augmentation)  
   - [Similar Classes](#similar-classes)  
3. [Model Architecture](#model-architecture)  
4. [Performance](#performance)  
5. [Deployment](#deployment)  
6. [Example Images](#example-images)

---

## Overview
This project focuses on automatically detecting **IMO/Dangerous Goods** stickers on shipping containers, each corresponding to specific hazardous material classes. The stickers are critical for:
- **Safety**: Ensuring hazardous materials are clearly identified.  
- **Compliance**: Meeting international regulations for transportation of dangerous goods.  
- **Operational Efficiency**: Streamlining port and vessel operations by automating cargo inspections.

We use an **SSD object detector** to localize and classify 20 different sticker types in real-world images. A key requirement was **robust detection** despite variations in sticker size, orientation, lighting, and container color.

---

## Dataset & Challenges

### Rare Classes & Augmentation
Out of the 20 classes, some appear infrequently in real-world shipments. This leads to **class imbalance**, making it hard for a model to learn robust features for those sticker types.  
- **Data Augmentation**: To mitigate this, artificial samples were created or existing samples were manipulated (e.g., rotation, scaling, color jitter, synthetic placements on container images).  
- **Result**: Improved representation of rare classes in the training set, leading to better recall and fewer missed detections.

### Similar Classes
Some classes have nearly identical designs, differing only in small text or icon details. For example, certain **Class 1** explosives subcategories (1.4, 1.5, etc.) can look quite alike, making it easy for a model to confuse them. To address this:
- **Fine-grained Features**: We ensured higher-resolution input for training or integrated specialized feature layers in the SSD network to capture subtle distinctions.  
- **High-quality Labels**: We rigorously curated and verified labels to avoid confusion during training.

---

## Model Architecture
We chose **SSD (Single Shot MultiBox Detector)** for the following reasons:
1. **Speed**: SSD performs object detection in a single forward pass, maintaining real-time or near real-time inference (∼50 ms).  
2. **Multi-scale Feature Maps**: SSD leverages multiple convolutional layers, enabling the model to detect objects of various sizes (stickers can be large or quite small).  
3. **End-to-End Training**: Simple pipeline that directly outputs bounding boxes and class probabilities without a separate region-proposal stage.

---

## Performance
- **Accuracy Improvement**: ~4–5% overall increase across the 20 classes after addressing the rare-class issue through augmentation and tuning.  
- **Inference Time**: ~50 ms per image, suitable for real-time or near-real-time applications in ports with high throughput.  
- **Production-Ready**: System is live in multiple ports worldwide, enabling automated checks for hazardous material stickers.

---

## Deployment
1. **Edge Computing**: The model can run on edge devices stationed at crane cameras or yard trucks for immediate detection.  
2. **Cloud or On-Prem Servers**: Optionally, images are sent to servers where the SSD model processes them in batch.  
3. **Integration**: Results are fed into logistics platforms to automate alerts and generate compliance reports.

---
