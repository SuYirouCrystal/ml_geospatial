# ATeX Image Classification — Result Comparison

This README reports our **test-set** performance using a lightweight timm model (MobileNetV3 Small) and compares it to **Table 1** baselines from the ATeX paper.

> **Our setup (from `task1.ipynb`)**  
> Backbone: `timm/mobilenetv3_small_100.lamb_in1k` · Image Size: 224 · Optimizer: Adam (lr=1e-4) · Epochs: 10 · Split: **test** for evaluation

---

## Our Test Metrics

| Metric | Value |
| --- | ---: |
| **Accuracy** | **84.91%** |
| **Macro Precision** | **84.05%** |
| **Macro Recall** | **83.21%** |
| **Macro F1** | **83.14%** |

---

## Per-Class Metrics (Test)

| Class | Precision | Recall | F1-score | Support |
|---|---:|---:|---:|---:|
| delta | 0.9403 | 0.9061 | 0.9228 | 330 |
| estuary | 0.8730 | 0.8800 | 0.8765 | 125 |
| flood | 0.8789 | 0.7951 | 0.8349 | 283 |
| glaciers | 0.9234 | 0.9542 | 0.9385 | 240 |
| hot_spring | 0.7991 | 0.8507 | 0.8241 | 201 |
| lake | 0.6442 | 0.8758 | 0.7424 | 153 |
| pool | 0.9394 | 0.7848 | 0.8552 | 79 |
| puddle | 0.8376 | 0.5833 | 0.6877 | 168 |
| rapids | 0.8502 | 0.8813 | 0.8655 | 219 |
| river | 0.7547 | 0.5479 | 0.6349 | 73 |
| sea | 0.7769 | 0.8704 | 0.8210 | 108 |
| snow | 0.7937 | 0.8944 | 0.8411 | 142 |
| swamp | 0.9365 | 0.9415 | 0.9390 | 188 |
| waterfall | 0.7812 | 0.7812 | 0.7812 | 96 |
| wetland | 0.8788 | 0.9355 | 0.9062 | 93 |

**Overall (from classification report)**

| Metric | Precision | Recall | F1-score | Support |
|---|---:|---:|---:|---:|
| **accuracy** | — | — | **0.8491** | **2498** |
| **macro avg** | 0.8405 | 0.8321 | 0.8314 | 2498 |
| **weighted avg** | 0.8545 | 0.8491 | 0.8478 | 2498 |

---

## Side-by-Side with Paper Baselines (ATeX Table 1)

> The paper’s “Accuracy” column is labeled **Accuracy (Val)**. Our accuracy is measured on the **test** split. Precision/Recall/F1 are **macro** metrics.

| Network | Train Time | LR | Epochs | Accuracy | Precision | Recall | F1 |
|---|---:|---:|---:|---:|---:|---:|---:|
| **Ours — MobileNetV3 Small (timm)** | — | 1.00E-04 | **10** | **84.91% (test)** | **84.05%** | **83.21%** | **83.14%** |
| Wide ResNet-50-2 | 0:06:56 | 2.50E-04 | 30 | 91% | 77% | 75% | 75% |
| VGG-16 | 0:04:38 | 2.50E-04 | 30 | 90% | 75% | 72% | 72% |
| SqueezeNet 1.0 | 0:00:47 | 7.50E-04 | 30 | 82% | 81% | 81% | 81% |
| ShuffleNet V2 x1.0 | 0:01:46 | 1.00E-02 | 30 | 90% | 90% | 90% | 90% |
| ResNeXt-50-32x4d | 0:03:15 | 2.50E-04 | 30 | 90% | 77% | 75% | 75% |
| ResNet-18 | 0:01:28 | 2.50E-04 | 30 | 87% | 74% | 72% | 72% |
| MobileNet V2 | 0:01:35 | 2.50E-04 | 30 | 88% | 74% | 72% | 72% |
| GoogLeNet | 0:01:51 | 5.00E-03 | 30 | 89% | 88% | 88% | 88% |
| EfficientNet-B7 | 0:12:42 | 1.00E-02 | 30 | 90% | **91%** | **91%** | **91%** |
| EfficientNet-B0 | 0:02:38 | 7.50E-03 | 30 | **91%** | 90% | 90% | 90% |
| DenseNet-161 | 0:06:15 | 2.50E-04 | 30 | **91%** | 81% | 79% | 79% |

**Summary:** Our quick 10-epoch run achieves **84.91% test accuracy** with **macro P/R/F1 ≈ 83–84%**, surpassing several paper baselines on macro metrics (e.g., VGG-16, ResNet-18, MobileNet V2, WRN-50-2, ResNeXt), and trailing the strongest EfficientNet/ShuffleNet/GoogLeNet results by ~4–6 points in accuracy.
