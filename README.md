# 🏛️ Discover Jordan: Classifying Heritage Sites Using Deep Learning

## 📌 Overview

This project uses deep learning and transfer learning techniques to classify images of key heritage sites in Jordan. By fine-tuning a pre-trained convolutional neural network on a custom dataset, the model achieves high accuracy in recognizing and promoting Jordan’s cultural landmarks through AI-powered image classification.

---

## 🇯🇴 Introduction

Jordan is home to some of the most remarkable heritage sites in the world, including **Petra**, **Jerash**, **the Dead Sea**, **Ajloun**, and **Wadi Rum**. These landmarks are not only historically and culturally significant, but also contribute greatly to tourism and national identity.

In this project, we leverage deep learning techniques to build an image classification model capable of recognizing and classifying images of **seven key heritage locations in Jordan**. This work demonstrates how AI can support cultural heritage preservation and digital tourism through computer vision.

---

## 🧠 Model Architecture

- **Base Model:** `ResNet50` (pre-trained on ImageNet)
- **Input Shape:** (224, 224, 3)
- **Fine-tuning Strategy:**  
  - First phase: freeze base model (15 epochs)  
  - Second phase: unfreeze top layers and fine-tune (15 epochs)
- **Loss Function:** `CategoricalCrossentropy`
- **Optimizer:** Adam (`lr=1e-5`)
- **Regularization:** Dropout(0.3)

<details>
<summary>Model Summary (Simplified)</summary>

```python
base_model = tf.keras.applications.ResNet50(
    input_shape=(224, 224, 3),
    include_top=False,
    weights='imagenet'
)
base_model.trainable = False

inputs = layers.Input(shape=(224, 224, 3))
x = data_augmentation(inputs)
x = base_model(x, training=False)
x = layers.GlobalAveragePooling2D()(x)
x = layers.Dense(128, activation='relu')(x)
x = layers.Dropout(0.3)(x)
outputs = layers.Dense(7, activation='softmax')(x)

model = tf.keras.Model(inputs, outputs)
