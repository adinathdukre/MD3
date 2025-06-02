
# 🧠 MD3: Toward Next-Generation Multi-Modal Multi-Class Deepfake Detection Benchmark

> **Paper:** _Toward Next-Generation Multi-Modal Deepfake Detection Benchmark_  
> [📄 PDF](https://github.com/adinathdukre/MD3) | [📊 Dataset Info](#dataset-overview) | [📬 Contact](#contact)

---

## ✨ Overview

**MD3** is a Toward Next-Generation, multimodal, and multiclass deepfake detection benchmark specifically designed to challenge and evaluate modern deepfake detectors. It addresses the **four core limitations** of existing benchmarks:

1. **Diversity Gap** – Current datasets focus on limited deepfake types (e.g., face-swapping)  
2. **Outdated Techniques** – Most deepfakes used are from older generation models  
3. **Simplistic Evaluation** – Binary classification dominates, while real-world needs require fine-grained detection  
4. **Insufficient Labels** – Most benchmarks fail to label forgery types explicitly

**MD3 introduces:**
- ✅ 8 unique audio-visual manipulation classes
- 🌍 Over 4,700 subjects from 114 countries
- 🧠 Compatibility with both binary and multiclass training
- 🎯 Evaluations on 8 state-of-the-art (SOTA) detection methods

---

## 📦 Dataset Overview

### 🔹 Forgery Types

| Modality | Category             | Techniques Used                         |
|----------|----------------------|------------------------------------------|
| Video    | Identity Swap (IS)   | SimSwap, FaceDancer                      |
| Video    | Expression Transfer  | FOMM, LivePortrait                       |
| Video    | Attribute Manip. (AM)| StyleGANEX, Latent Transformer          |
| Audio    | Voice Cloning (TTS)  | StyleTTS, HierSpeech++                  |
| Visual+Audio | Fully Synthetic  | All combinations of above               |

- 🔢 **Real Audio + Real Video:** 40K clips from VoxCeleb2  
- 🔁 **Fake Pairs (AV):** 140K synthetic videos + 80K synthetic audios  
- 🧬 Covers IS, ET, AM, and TTS for wide modality coverage

---

### 📊 Dataset Composition & Modalities

![MD3 Figure 1](assert/motivation_cropped.pdf)  
*Figure 1: Overview of multi-modal data combinations used in MD3.*

![MD3 Figure 2](assets/sample_ from each_class.pdf)  
*Figure 2: Comparison of class balance and subject diversity with other datasets.*

---

## 📊 Benchmark Results

### Multiclass Classification (Image-based)

| Model              | Classes | Accuracy | AUC  | Precision | Recall | F1    |
|--------------------|---------|----------|------|-----------|--------|-------|
| Xception           | 4       | 71.58%   | 0.90 | 72.81     | 71.59  | 71.72 |
| MesoInception4     | 4       | 39.88%   | 0.74 | 53.44     | 39.76  | 35.75 |

### Binary Classification (Audio-Visual)

| Dataset     | Method       | Modality | AUC  |
|-------------|--------------|----------|------|
| FakeAVCeleb | AVFF-CVPR24  | AV       | 99%  |
| **MD3**     | AVFF-CVPR24  | AV       | 87%  |

---

## 🔁 Dataset Construction Pipeline

- **Source Data:** VoxCeleb2 (interviews with clear, unobstructed, English-speaking faces)
- **Manipulations:** Applied per-frame or per-audio clip using:
  - Deepfake generators (SimSwap, FaceDancer, FOMM, StyleGANEX)
  - Voice cloning (StyleTTS, HierSpeech++)
- **Combinations:** Real/Fake audio + Real/Fake video → 10 possible pairs
- **Ethnic & Gender Stratification:** Ensures balanced demographics

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
```

---


---


---

## 📬 Contact

- ✉️ Adinath Dukre (MBZUAI) – `adinath.dukre@mbzuai.ac.ae`

---

