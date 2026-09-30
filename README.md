# Understanding Which Image Distortions Break OCR First

**Project ID:** ML-T2-062  
**Track:** Track 2 – Advanced Machine Learning Internship  
**Domain:** Computer Vision / Optical Character Recognition

## Overview

This project investigates how controlled image distortions affect Optical Character Recognition (OCR) performance and evaluates whether distortion-specific preprocessing can recover recognition accuracy.

The experiment uses the **FUNSD (Form Understanding in Noisy Scanned Documents)** dataset and **PaddleOCR** as the fixed OCR engine.

## Objectives

- Evaluate OCR performance on clean document images.
- Study the effect of different image distortions on OCR.
- Measure OCR performance using Character Error Rate (CER) and Word Error Rate (WER).
- Apply targeted preprocessing for each distortion.
- Compare OCR performance before and after preprocessing.

## Dataset

**Dataset:** FUNSD – Form Understanding in Noisy Scanned Documents

A controlled sample of **50 images** was selected using random seed `42`. Ground-truth text was obtained from the corresponding FUNSD JSON annotations.

## Experimental Setup

### OCR Engine
- PaddleOCR

### Evaluation Metrics
- Character Error Rate (CER)
- Word Error Rate (WER)

### Tested Distortions

| Distortion | Configuration |
|---|---|
| Gaussian Blur | 9 × 9 kernel |
| Gaussian Noise | Standard deviation = 25 |
| Low Contrast | α = 0.45, β = 20 |

### Targeted Preprocessing

| Distortion | Preprocessing |
|---|---|
| Blur | Sharpening |
| Noise | Fast Non-Local Means Denoising |
| Low Contrast | CLAHE |

## Experimental Pipeline

```text
FUNSD Image
     ↓
Ground-Truth Text
     ↓
Clean Image OCR
     ↓
Apply Image Distortion
     ↓
Distorted Image OCR
     ↓
Targeted Preprocessing
     ↓
Preprocessed Image OCR
     ↓
Calculate CER and WER
     ↓
Compare Results
