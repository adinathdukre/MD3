
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
## 📦 Highlighting Our Dataset

### Highlighting Our Dataset

This radar chart showcases the comparative strengths of our dataset across multiple dimensions, including multiclass coverage, AV modality balance, number of subjects, and advanced manipulation types.  
Our dataset significantly expands the landscape compared to existing benchmarks, offering a more comprehensive and challenging resource for deepfake detection research.

![Highlighting Our Dataset](assets/Highlightin_Our_Dataset_.png)
![Highlighting Our Dataset](assert/Highlightin_Our_Dataset_.png)



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


## 🔁 Dataset Construction Methodology

The MD3 dataset is derived from the VoxCeleb2 corpus, containing high-resolution interview recordings of over 6,000 celebrities. To ensure linguistic consistency, the OpenAI Whisper model was employed to filter and retain only English-speaking individuals—a process that required approximately two days using an NVIDIA A6000 GPU with 48GB of memory.

Subsequently, 12 annotators reviewed and selected video segments (1–10 minutes per subject) using a custom video playback interface at 2x speed. The selection criteria emphasized single-person presence, frontal face visibility, absence of obstructions (e.g., hats, glasses), high video quality, and English speech.

A team of four annotators manually stratified the subjects into ethnic groups to ensure balanced demographic representation. In total, over 33,000 high-quality real audio-visual clips were curated.

For synthetic data generation, eight distinct deepfake techniques were employed across both video and audio domains. These manipulations were performed using over 2,000 GPU-hours on A6000 GPUs. To enhance the realism of the manipulations, each target subject was paired with five source identities matched by both gender and ethnicity. The **DeepFace** facial recognition library was employed to compute identity similarity scores, ensuring high facial consistency prior to manipulation. This consistency filtering mitigated the risk of generating low-quality, easily detectable fakes, particularly in cross-ethnic or cross-gender scenarios.

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
