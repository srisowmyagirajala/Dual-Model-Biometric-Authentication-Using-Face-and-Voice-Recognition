# Dual-Model Biometric Authentication Using Face and Voice Recognition

## Overview
This project presents a biometric authentication system that integrates face recognition and voice recognition for secure, real-time identity verification.  
Unlike traditional password- or PIN-based systems, this approach leverages deep learning models to achieve higher accuracy, even under challenging conditions such as masked faces and noisy environments.  

---

## Features
- Dual-model authentication using:
  - FaceNet and ArcFace for face recognition  
  - Wav2Vec2 and ECAPA-TDNN for voice recognition  
- Preprocessing with CLAHE, normalization, and noise filtering  
- Real-time face capture using a JavaScript-based webcam module (MTCNN for detection)  
- Weighted fusion strategy: 60% face + 40% voice with adaptive thresholds  
- Robust against masked/unmasked faces and noisy audio inputs  
- Fast authentication decisions within seconds  

---

## Dataset
- 25 individuals included  
- Masked and unmasked facial images  
- 5 voice recordings per individual  
- Preprocessing steps:
  - Contrast Limited Adaptive Histogram Equalization (CLAHE)  
  - Resizing and normalization  
  - Noise filtering  

---

## Methodology

### Feature Extraction
- Face:  
  - FaceNet → 128-dim embeddings  
  - ArcFace → margin-based embeddings  
- Voice:  
  - Wav2Vec2 and ECAPA-TDNN → 256-dim embeddings  

### Biometric Fusion & Authentication
- L2-normalized embeddings  
- Cosine similarity for comparison  
- Fusion rule:  
  \[
  Score = 0.6 \times Face + 0.4 \times Voice
  \]  
- Access granted if score ≥ 80% threshold  

### Real-Time Implementation
- Face input: Webcam (via JS module)  
- Voice input: Microphone  
- Authentication decision within seconds  

---

## Experimental Results

### Face Recognition
| Model    | Unmasked | Masked |
|----------|----------|--------|
| FaceNet  | 93.91%   | 89.70% |
| ArcFace  | 81.70%   | 69.20% |

### Voice Recognition
- Accuracy: 98.20% (stable across all conditions)  

### Combined Biometric Accuracy
| Combination       | Unmasked | Masked |
|------------------|----------|--------|
| FaceNet + Voice  | 95.63%   | 93.10% |
| ArcFace + Voice  | 88.30%   | 80.80% |

---

## Applications
- Healthcare – Secure access for patients and staff, telemedicine authentication  
- Mobile Devices – Enhanced smartphone/tablet unlocking  
- Banking & Finance – High-security verification for online transactions  
- Attendance Systems – Reliable authentication in academic and corporate settings  

---

## Future Work
- Adaptive fusion strategies for varying light and noise conditions  
- Integration of deepfake detection and liveness checks  
- Expansion to larger, more diverse datasets for real-world scalability  

---

## References
1. Schroff et al., *FaceNet: A Unified Embedding for Face Recognition and Clustering*, 2015  
2. Deng et al., *ArcFace: Additive Angular Margin Loss for Deep Face Recognition*, 2019  
3. Perrot et al., *Multi-modal Biometric Authentication: A Survey on Face and Voice Fusion Techniques*, 2022  

---

## Tech Stack
- Python, Torch, Librosa, OpenCV, SpeechBrain, DeepFace, InsightFace  
- JavaScript (Webcam capture)  
- MTCNN, ONNX Runtime  
