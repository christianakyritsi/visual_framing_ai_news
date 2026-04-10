# 📰 Visual Framing of AI in News Media

Unsupervised clustering pipeline to analyze how AI is visually represented across major news outlets, using ~200 images scraped from NOS, NU.nl, New York Times, and Reuters.

## 📌 Overview

The central research question driving this project is: **How do news media visually frame AI?** By extracting low-level visual features and applying unsupervised clustering, the project uncovers patterns in how different outlets portray artificial intelligence — without any manual labelling.

## 🔍 Approach

- 🎨 **Feature Extraction** — brightness (grayscale), edge density (Canny), texture strength (Sobel), and color histograms (16 bins per RGB channel)
- 🤖 **Object Detection** — Faster R-CNN to detect objects present in each image
- 📉 **PCA + K-Means** — dimensionality reduction to 95% explained variance, k=5 selected via elbow method
- 🗺️ **UMAP + DBSCAN** — 2D non-linear projection followed by density-based clustering

## 🏷️ Cluster Labels (PCA + K-Means, k=5)

| Cluster | Label | Description |
|---|---|---|
| 0 | Outlier | Single image, likely anomaly |
| 1 | Sceneries & Minimal Objects | Moderate brightness, balanced colors, few people |
| 2 | Human-Focused, Intense | High contrast, neon tones, dense texture, people present |
| 3 | Clean & Minimal | White backgrounds, discrete colors, low object diversity |
| 4 | Tech-Focused | High object density, machinery and tech-related content |

## 📊 Cluster Distribution (PCA + K-Means)

| Cluster | Image Count |
|---|---|
| 0 | 21 |
| 1 | 52 |
| 2 | 78 |
| 3 | 12 |
| 4 | 35 |

> 💡 Outlet distribution across clusters (NOS, NU.nl, NYT, Reuters) was roughly uniform, suggesting clusters reflect **visual content** rather than publisher style.

## 🛠️ Tech Stack

`Python` `OpenCV` `Faster R-CNN` `UMAP` `DBSCAN` `K-Means` `PCA` `scikit-learn`

## 📂 Dataset

~200 images sampled from online news articles about artificial intelligence across four outlets: NOS, NU.nl, New York Times, and Reuters.
