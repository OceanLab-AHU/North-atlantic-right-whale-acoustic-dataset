# North-atlantic-right-whale-acoustic-dataset for overlapping sound event detection

This repository hosts a whale acoustic dataset constructed using real-world **North Atlantic Right Whale (NARW)** vocalization recordings. The dataset is specifically designed to evaluate detection performance in complex underwater environments characterized by multi-source overlap and varying signal-to-noise ratio (SNR) conditions.

## 📊 Dataset Overview

### 1. Preprocessing and Stratification
* **Audio Specifications**: All samples are amplitude-normalized and resampled to **8 kHz**.
* **Vocalization Types**: The foreground library contains four NARW vocalization types: **Upcalls, Gunshots, Screams, and Moancalls**.
* **Background Noise**: Extracted from non-event intervals within the same recording batches to ensure environmental consistency.
* **Data Split**: The source data is divided into training, validation, and test sets using a **7:1.5:1.5 ratio** to prevent data leakage.

### 2. Event Characteristics 
A core challenge of this dataset is the significant variation in duration across different event types, which complicates the detection of overlapping signals:

| Category | Count | Event Duration (s) | Occurrence Prob. | Events per Occurrence |
| :--- | :--- | :--- | :--- | :--- |
| **Upcall** | 224 | 1.5 ± 0.5 | 100% | 1–2 |
| **Gunshot** | 176 | 0.8 ± 0.3 | 100% | 1–2 |
| **Scream** | 200 | 2.1 ± 0.7 | 85% | 1–2 |
| **Moancall** | 191 | 4.2 ± 1.8 | 75% | 1 |

### 3. Synthesis and Overlap Settings
* **Segment Duration**: Events are synthesized into 10-second audio clips.
* **Overlap Generation**: Start times are sampled uniformly within the [0, 10]s interval relative to duration, resulting in high-density overlapping events, particularly between **Upcalls** and **Gunshots**.

## 🔊 SNR Levels and Distribution 

To reflect real-world underwater statistical likelihoods, the dataset adopts a 2:3:3:2 distribution across four SNR levels. Notably, it includes a challenging **Very Low SNR ([-10, -5] dB)** category:

| SNR Level | Range (dB) | Train | Val | Test | Total |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **SNR_H (High)** | [5, 10] | 1,400 | 300 | 300 | 2,000 |
| **SNR_M (Medium)** | [0, 5] | 2,100 | 450 | 450 | 3,000 |
| **SNR_L (Low)** | [-5, 0] | 2,100 | 450 | 450 | 3,000 |
| **SNR_VL (Very Low)** | **[-10, -5]** | 1,400 | 300 | 300 | 2,000 |
| **Total** | - | **7,000** | **1,500** | **1,500** | **10,000** |

## 📥 Data Access

Due to the total file size exceeding 1GB, the dataset is available via the following methods:

**Zenodo**: [https://doi.org/10.5281/zenodo.1234567](https://doi.org/10.5281/zenodo.1234567)

