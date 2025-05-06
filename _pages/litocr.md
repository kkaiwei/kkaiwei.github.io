---
layout: page
title: "LitOCRé"
permalink: /litocr/
---

# LitOCRé  
## Integrating ResNet and TrOCR with LoRA Fine‑Tuning for French Handwritten Text Recognition

**Hazel Chen**  
Stanford University Center for Spatial and Textual Analysis

## Abstract

Handwritten literature from the 19th century holds significant cultural value, yet its digitization poses unique challenges due to the diversity of cursive writing styles and document degradation. To address this, we introduce **LitOCRé: A Two‑Stage Deep Learning System for Transcribing 19th‑Century French Handwritten Literature**. Our approach combines ResNet‑based text localization and fine‑tuned TrOCR‑based text recognition, enhanced with LoRA (Low‑Rank Adaptation) fine‑tuning for robust performance.

The first stage utilizes a ResNet‑based object detection model to accurately identify text regions within scanned manuscript pages, effectively handling variations in handwriting and layout. The second stage processes these localized text segments using a fine‑tuned TrOCR model, leveraging LoRA to adapt cross‑attention layers and final encoder layers to the stylistic nuances of 19th‑century French cursive.

LitOCRé demonstrates significant improvements in text recognition accuracy, outperforming conventional OCR methods on challenging handwritten texts. The system’s modular design allows for fine‑tuning and adaptation to other handwritten languages, offering a powerful solution for digitizing historical literary archives.

## Methods

![Pipeline](/images/litocr-teaser.jpg)

### Stage 1: Text Localization

The first stage of LitOCRé focuses on detecting text regions within scanned manuscript pages. We employ a ResNet‑based object detection model, leveraging convolutional layers to extract visual features. A Region Proposal Network (RPN) generates bounding boxes around potential text areas, and a detection head refines these boxes to accurately localize handwritten text.

The model is fine‑tuned using a curated dataset of 19th‑century French manuscripts. To improve robustness, data augmentation techniques like rotation and noise addition are applied. The training process minimizes classification and bounding box regression losses using an SGD optimizer with a learning rate scheduler. 

### Stage 2: Text Recognition

Once text regions are localized, we use a fine‑tuned TrOCR model for transcription. TrOCR combines a Vision Transformer (ViT) encoder and a Transformer decoder to model visual and textual information. To adapt to diverse handwriting styles, we apply LoRA fine‑tuning specifically to cross‑attention layers and the final encoder layers.

The training process involves initializing with a pre‑trained TrOCR model and fine‑tuning on 19th‑century French handwritten data. The model optimizes using AdamW and Connectionist Temporal Classification (CTC) loss. LoRA fine‑tuning ensures domain‑specific adaptation without overfitting, enhancing the model’s ability to recognize nuanced cursive handwriting.

## BibTeX

If you find it helpful, please consider citing our work:

```bibtex
@inproceedings{chen2025litocre,
  author   = {Hazel Chen},
  title    = {LitOCRé: A Two‐Stage Deep Learning System for Transcribing 19th‐Century French Handwritten Literature},
  keywords = {OCR, Handwritten Text Recognition, French Literature, ResNet, TrOCR, LoRA, Cultural Heritage},
  url      = {https://kkaiwei.github.io/litocr},
}
