# A Multitask Framework for Cyberbullying Detection in Multi-modal Code-Mixed Memes

## Overview

In this project, we propose a multitask framework that combines sentiment analysis, emotion detection, sarcasm recognition, and cyberbullying identification. By leveraging multi-modal inputs from memes, we aim to enhance detection accuracy and better understand the nuances of online interactions.

## Dataset

Our dataset comprises the following components:

1. **[Text Annotations](https://docs.google.com/spreadsheets/d/1tD5yqGZ3TlDjeUFThautfZGegHrRz7FW/edit?usp=sharing&ouid=110763476686692440605&rtpof=true&sd=true)**:
   - Includes annotations for Bullying, Sentiment, Emotion, Sarcasm, Target, and Harmfulness Score.
   
2. **[Meme Images](https://drive.google.com/drive/folders/1GEj1vjcZpSFcHiHkzxxSwQpeOBp_TXY5?usp=sharing)**:
   - A collection of memes used for training and evaluation.

## Model Training

### Training Strategy

1. **Multitask Learning**:
   - Train the model on auxiliary tasks (Emotion, Sentiment, Sarcasm) alongside the main task (Bully detection) using a central network to optimize the loss function for all tasks simultaneously.
  
2. **Overfitting Prevention**:
   - Start by training the model on individual tasks to mitigate overfitting due to model complexity.
   - Tasks include:
     - Bully Detection
     - Sentiment Analysis
     - Emotion Detection
     - Sarcasm Detection
  
3. **Fine-tuning**:
   - After pretraining on individual tasks, load the pretrained weights and freeze the corresponding layers. Only the Central Network's weights are updated during training.
   - Model selection for training can be customized [here](https://github.com/Deep-cx-01/MultiBully/blob/9a35c4cc7bfdcbea00a9661fbd77bff69fdc1e12/train.py#L258).

### Task-Specific Implementations

- You can choose to freeze or fine-tune parameters for specific tasks:
  - [Emotion](https://github.com/Deep-cx-01/MultiBully/blob/9a35c4cc7bfdcbea00a9661fbd77bff69fdc1e12/centralnet.py#L240)
  - [Sarcasm](https://github.com/Deep-cx-01/MultiBully/blob/9a35c4cc7bfdcbea00a9661fbd77bff69fdc1e12/centralnet.py#L247)
  - [Sentiment](https://github.com/Deep-cx-01/MultiBully/blob/9a35c4cc7bfdcbea00a9661fbd77bff69fdc1e12/centralnet.py#L253)
  - [Bully](https://github.com/Deep-cx-01/MultiBully/blob/9a35c4cc7bfdcbea00a9661fbd77bff69fdc1e12/centralnet.py#L258)

## References

We recommend reading the following papers in the specified order to build a foundational understanding before diving into the code:

1. [CLIP](https://arxiv.org/pdf/2103.00020.pdf)
2. [The Verbal and Non Verbal Signals of Depression](https://arxiv.org/pdf/1904.07656.pdf)
3. [CentralNet: a Multilayer Approach for Multimodal Fusion](https://arxiv.org/pdf/1808.07275.pdf)
4. [MOMENTA](https://aclanthology.org/2021.findings-emnlp.379.pdf)

## Code Sources

We’ve utilized code from the following sources, which you can explore for additional insights:

1. [CLIP Feature Extractor](https://github.com/openai/CLIP)
2. [CentralNet Code](https://github.com/jperezrua/mfas)
3. [MOMENTA](https://github.com/lcs2-iiitd/momenta)
