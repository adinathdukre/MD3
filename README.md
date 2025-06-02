# 🧠 MD3: Toward Next-Generation Multi-Modal Multi-Class Deepfake Detection Benchmark

> **Paper:** _Toward Next-Generation Multi-Modal Deepfake Detection Benchmark_  
> [📄 PDF](https://github.com/adinathdukre/MD3) | [📊 Dataset Info](#dataset-overview) | [📬 Contact](#contact)

---

## ✨ Overview

**MD3** is a next-generation multimodal, multiclass deepfake detection benchmark designed to challenge and evaluate modern deepfake detectors. It addresses **four key limitations** of existing benchmarks:

1. **Diversity Gap** – Existing datasets focus on limited deepfake types (e.g., face swapping)  
2. **Outdated Techniques** – Most datasets use older-generation deepfake models  
3. **Simplistic Evaluation** – Benchmarks are often binary, but real-world tasks demand fine-grained classification  
4. **Insufficient Labels** – Few benchmarks provide detailed forgery-type labels

**MD3 introduces:**
- ✅ 8 unique audio-visual manipulation classes
- 🌍 Over 4,700 subjects from 114 countries
- 🧠 Support for both binary and multiclass training
- 🎯 Benchmarking on 8 state-of-the-art (SOTA) detection methods

---

## 📦 Dataset Overview

### 🔹 Forgery Types

| Modality       | Category              | Techniques Used                      |
|---------------|-----------------------|--------------------------------------|
| Video         | Identity Swap (IS)    | SimSwap, FaceDancer                  |
| Video         | Expression Transfer   | FOMM, LivePortrait                   |
| Video         | Attribute Manip. (AM) | StyleGANEX, Latent Transformer       |
| Audio         | Voice Cloning (TTS)   | StyleTTS, HierSpeech++               |
| Audio + Video | Fully Synthetic       | Combinations of the above            |

- 🔢 **Real Audio + Real Video:** 40K clips from VoxCeleb2  
- 🔁 **Fake Pairs (AV):** 140K synthetic videos + 80K synthetic audios  
- 🧬 Comprehensive coverage: IS, ET, AM, TTS for rich modality combinations

---

### 📊 Dataset Composition & Modalities

![Sample from each class](assert/sample_%20from%20each_class_page-0001.jpg)
 
*Figure 1: Overview of multi-modal data combinations used in MD3.*

![Class sample distribution](assert/class%20sample%20distribution_page-0001.jpg)
 
*Figure 2: Class balance and subject diversity compared with other datasets.*

---

## 📊 Benchmark Results

### Multiclass Classification (Image-based)

| Model            | Classes | Accuracy | AUC  | Precision | Recall | F1    |
|------------------|---------|----------|------|-----------|--------|-------|
| Xception         | 4       | 71.58%   | 0.90 | 72.81     | 71.59  | 71.72 |
| MesoInception4   | 4       | 39.88%   | 0.74 | 53.44     | 39.76  | 35.75 |

### Binary Classification (Audio-Visual)

| Dataset      | Method        | Modality | AUC  |
|-------------|---------------|----------|------|
| FakeAVCeleb | AVFF-CVPR24   | AV       | 99%  |
| **MD3**     | AVFF-CVPR24   | AV       | 87%  |

---

## 🔁 Dataset Construction Pipeline

- **Source Data:** VoxCeleb2 (interviews with clear, unobstructed, English-speaking faces)
- **Manipulations:** Applied per frame or per audio clip using:
  - Deepfake generators (SimSwap, FaceDancer, FOMM, StyleGANEX)
  - Voice cloning models (StyleTTS, HierSpeech++)
- **Combinations:** Real/Fake audio + Real/Fake video → 10 possible AV pairings
- **Ethnic & Gender Stratification:** Ensures demographic balance

---



## 🏗 Repo Structure

```bash
MD3/
├── dataset/             # Dataset generation scripts or links
├── models/              # Detection model implementations (Xception, Meso, etc.)
├── results/             # Evaluation outputs and metrics
├── assets/              # Figures, thumbnails, samples
├── requirements.txt     # Dependency file
└── README.md
