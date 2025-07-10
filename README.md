# 🏛️ Discover Jordan: Classifying Heritage Sites Using Deep Learning

This project uses deep learning and transfer learning techniques to classify images of key heritage sites in Jordan. By fine-tuning a pre-trained convolutional neural network on a custom dataset, the model achieves high accuracy in recognizing and promoting Jordan’s cultural landmarks through AI-powered image classification.
## 🇯🇴 Introduction

Jordan is home to some of the most remarkable heritage sites in the world, including **Petra**, **Jerash**, **the Dead Sea**, **Ajloun**, and **Wadi Rum**. These landmarks are not only historically and culturally significant, but also contribute greatly to tourism and national identity.

In this project, we leverage deep learning techniques to build an image classification model capable of recognizing and classifying images of **seven key heritage locations in Jordan**.
## 🧠 Model Architecture

- **Base Model:** `ResNet50` (pre-trained on ImageNet)
- **Input Shape:** (224, 224, 3)
- **Fine-tuning Strategy:**  
  - First phase: freeze base model (15 epochs)  
  - Second phase: unfreeze top layers and fine-tune (15 epochs)
- **Loss Function:** `CategoricalCrossentropy`
### Note:
- **Total Images:** 328
-**Number of Classes:** 7
-**Class Labels:** Dead_Sea, Petra, Roman_Theater, Wadi_Rum, ajloun, dana, jarash
