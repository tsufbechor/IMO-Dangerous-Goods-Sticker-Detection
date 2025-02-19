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

![image](https://github.com/user-attachments/assets/4a107f22-1243-4d14-9026-b0ff67e93afe)

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


---

## Performance
- **Accuracy Improvement**: ~4–5% overall increase across the 20 classes after addressing the rare-class issue through augmentation and hyper parameter tuning.  
- **Inference Time**: ~50 ms per image, suitable for real-time or near-real-time applications in ports.  
- **Production-Ready**: System is live in multiple ports worldwide

## Examples

![image](https://github.com/user-attachments/assets/1859c6a7-7ca0-4a58-8c0e-c7969a214d20)
![image](https://github.com/user-attachments/assets/b31e0c59-08dc-4034-b3ab-8d82d208f2b0)

---

---
