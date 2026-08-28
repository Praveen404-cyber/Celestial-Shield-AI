<div align="center">

# 🛡️ Celestial Shield AI
<img width="2928" height="230" alt="Celestial Shiled" src="https://github.com/user-attachments/assets/8dea1c9a-c04a-4a09-ba1e-797bf6c0965c" />

### Machine Learning–Powered Phishing & Smishing Detection System

[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)](https://www.python.org/)
[![GUI](https://img.shields.io/badge/Interface-Tkinter-orange)]()
[![ML](https://img.shields.io/badge/Model-TF--IDF%20%2B%20Logistic%20Regression-green)]()
[![Accuracy](https://img.shields.io/badge/Accuracy-93%25-brightgreen)]()
[![Status](https://img.shields.io/badge/Status-Academic%20Final%20Project-yellow)]()

*A privacy-first, fully offline desktop application that detects email phishing and SMS smishing attempts using explainable machine learning — built for real people, not just security experts.*

</div>

---

## 📖 Table of Contents
1. [Overview](#-overview)
2. [The Problem](#-the-problem)
3. [Key Features](#-key-features)
4. [How It Works](#-how-it-works)
5. [System Showcase](#-system-showcase)
6. [Tech Stack](#-tech-stack)
7. [Machine Learning Methodology](#-machine-learning-methodology)
8. [Model Performance](#-model-performance)
9. [Core Logic Snippets](#-core-logic-snippets)
10. [Getting Started](#-getting-started)
11. [Usage Guide](#-usage-guide)
12. [Limitations & Future Work](#-limitations--future-work)
13. [Academic Context](#-academic-context)
14. [License](#-license)
15. [Author](#-author)

---

## 🔍 Overview

**Celestial Shield AI** is a standalone desktop application built to identify email-based phishing and SMS-based smishing (SMS phishing) messages. Rather than exposing users to a raw, unexplained "malicious / not malicious" verdict, it translates the underlying model's probability output into structured, human-readable risk levels — **Low**, **Medium**, and **High** — backed by confidence percentages and color-coded visual indicators.

The goal is to close the gap between machine learning research and everyday usability: most phishing detection tools are built for technical evaluation, not for the non-technical users who are actually targeted by these attacks. Celestial Shield AI is designed with that audience in mind.

## ⚠️ The Problem

Phishing and smishing attacks continue to succeed largely because they exploit **psychology, not technology** — urgency, fear, financial incentive, and impersonation of trusted institutions. Non-technical users, who make up the majority of targets, often have no reliable way to judge whether a message is safe. Celestial Shield AI addresses this by:

- Giving users a clear, structured verdict instead of a confusing technical output
- Explaining *why* a message was flagged (identified keywords and URLs)
- Operating entirely offline, so sensitive message content never leaves the user's device

## ✨ Key Features

| Feature | Description |
|---|---|
| 🎯 **Unified Threat Detection** | Analyzes textual patterns across both email and SMS inputs using a single classification pipeline |
| 📊 **Structured Risk Interpretation** | Converts raw probability scores into Low / Medium / High risk categories instead of a forced binary decision |
| 🎨 **Visual Confidence Indicators** | Dynamic, color-coded progress bars (green / orange / red) for at-a-glance interpretation |
| 📝 **On-Demand Security Reporting** | Generates timestamped `.txt` reports summarizing the classification and advisory notes, for personal record-keeping |
| 🔒 **Privacy-First Architecture** | Fully offline; session-based memory only — no message content is ever stored permanently or transmitted externally |
| 📈 **Real-Time Analytics** | In-app statistics tab tracking safe vs. malicious scans and model details for the current session |
| 📦 **Batch Processing** | Experimental support for analyzing multiple messages in a single pass |

## ⚙️ How It Works

```
 Raw Message (Email / SMS)
        │
        ▼
 Text Preprocessing   ── lowercase, strip URLs/numbers/symbols, remove stopwords
        │
        ▼
 TF-IDF Vectorization ── converts cleaned text into weighted numerical features
        │
        ▼
 Logistic Regression  ── predicts class + probability (confidence score)
        │
        ▼
 Risk Mapping Layer   ── combines prediction + confidence + keyword rules → Low / Medium / High
        │
        ▼
 GUI Output           ── color-coded verdict, confidence bar, advisory tip, optional report
```

## 📸 System Showcase

**Main Interface**

<img width="1917" height="1030" alt="Dashboard" src="https://github.com/user-attachments/assets/4955e1fb-50e5-41d3-8dc7-343127e79ef8" />

> The split-panel dashboard separates message input from classification results and security advisories for maximum readability.

**High Risk — Smishing Detected (Dark Mode)**

<img width="1918" height="1031" alt="Smishing Detection" src="https://github.com/user-attachments/assets/ba8ef0e5-a116-4b65-98ce-7e3ffe312576" />

> A confirmed smishing attempt, flagged with a red confidence bar and an immediate "DO NOT" advisory.

**High Risk — Phishing Detected (Dark Mode)**

<img width="1919" height="1030" alt="Phishing Detection" src="https://github.com/user-attachments/assets/618c1b49-c7df-4185-9659-47f293d78bd3" />

> A confirmed phishing attempt, with identified suspicious URLs and keywords surfaced alongside the verdict.

**Medium Risk — Suspicious**

<img width="1916" height="1031" alt="Suspicious Message" src="https://github.com/user-attachments/assets/4ab7e58e-e920-4ec2-9976-fad4da37430f" />

> A borderline message assigned a Medium risk level, prompting the user to verify the source before acting.

**Low Risk — Safe**

<img width="1917" height="1031" alt="Safe Message" src="https://github.com/user-attachments/assets/9fd0e7c1-6ab9-49df-9806-234c08180ac6" />

> A legitimate message correctly classified as Low risk, with no strong threat indicators found.

**Batch Processing**

<img width="1918" height="1031" alt="Batch Processing" src="https://github.com/user-attachments/assets/01ff3f38-45cd-41a7-8ab4-5dff6432b39c" />

> Experimental multi-message analysis for scanning several inputs in one pass.

**Statistics Dashboard**

<img width="1915" height="1027" alt="Statistics" src="https://github.com/user-attachments/assets/ad58851d-539d-4919-90e6-6f263e6a46fd" />

> Real-time session statistics showing model details and a breakdown of safe vs. malicious scans.

**Report Generation**

<img width="665" height="613" alt="Report Generation" src="https://github.com/user-attachments/assets/74fd4513-36dc-40a3-9579-a9f74a2ae12d" />

> A structured, timestamped `.txt` report including the classification result and relevant advisory notices.

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python |
| GUI | Tkinter (desktop) |
| Feature Extraction | TF-IDF (Term Frequency–Inverse Document Frequency) |
| Classification | Logistic Regression |
| Deployment | Standalone, fully offline desktop application |

## 🧠 Machine Learning Methodology

The detection engine is built on **supervised text classification**:

- **TF-IDF Vectorization** measures how important a word is to a specific message relative to the full dataset, surfacing terms strongly associated with malicious intent (urgency phrases, suspicious links, financial bait, etc.).
- **Logistic Regression** was chosen over more complex models because it (a) produces interpretable probability outputs — essential for the confidence-score UI — and (b) is computationally lightweight, a hard requirement for a responsive, fully offline desktop tool with no GPU dependency.

The model was trained and validated on publicly available datasets containing labeled phishing, smishing, and legitimate messages.

## 📊 Model Performance

| Metric | Score |
|---|---|
| Accuracy | **93%** |
| Precision (Weighted Avg) | **93%** |
| Recall (Weighted Avg) | **93%** |
| F1-Score (Weighted Avg) | **93%** |

## 💻 Core Logic Snippets

> The full source code is kept private to protect academic and intellectual property rights. The snippets below illustrate the core preprocessing and decision pipeline.

**1. Text Preprocessing (Noise Reduction)**

```python
def clean_text(text, remove_stopwords=True):
    if not isinstance(text, str):
        return ""
    text = text.lower()
    text = re.sub(r'http\S+|www\.\S+', ' url ', text)
    text = re.sub(r'\d+', ' num ', text)
    text = re.sub(r'[^a-z\s]', ' ', text)
    text = re.sub(r'\s+', ' ', text).strip()

    if remove_stopwords:
        tokens = [word for word in text.split() if word not in STOPWORDS]
        return " ".join(tokens)
    return text
```

**2. Risk Classification & Decision Logic**

```python
# Transform text and predict
clean = clean_text(msg)
vec = vectorizer.transform([clean])

ml_pred = clf.predict(vec)[0]
probs = clf.predict_proba(vec)[0]
confidence = max(probs)

# Security-first decision logic
if ml_pred in ["phishing", "smishing"]:
    final_label = ml_pred.upper()
    risk = "High"
    tip = "⚠️ WARNING: DO NOT click links, download attachments, or reply."
elif confidence < 0.75 and any(k in text_lower for k in SUSPICIOUS_KEYWORDS):
    final_label = "SUSPICIOUS"
    risk = "Medium"
    tip = "CAUTION: Suspicious elements detected. Verify with official source."
else:
    final_label = "SAFE"
    risk = "Low"
    tip = "This message appears safe. No strong threat indicators detected."
```

## 🚀 Getting Started

> ⚠️ Adjust file/folder names below if they differ from your actual repository layout.

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/celestial-shield-ai.git
cd celestial-shield-ai

# 2. (Recommended) Create a virtual environment
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run the application
python main.py
```

## 📘 Usage Guide

1. Launch the application — the split-panel dashboard opens.
2. Paste or type the email/SMS message you want to check into the input panel.
3. Click **Analyze** to run the message through the detection pipeline.
4. Review the result: risk level (Low / Medium / High), confidence percentage, and any flagged keywords or URLs.
5. Optionally generate a timestamped `.txt` report for your own records.
6. Check the **Statistics** tab for a running summary of the current session's scans.

## 🔭 Limitations & Future Work

- **Dataset generalization** - performance depends on the diversity of the training data; novel or region-specific phishing patterns may be underrepresented.
- **Language coverage** - the current model is trained primarily on English-language text.
- **Model complexity** - Logistic Regression was chosen for speed and interpretability; future iterations could explore transformer-based models for higher accuracy at the cost of resource usage.
- **Deployment scope** - currently a desktop application; a browser extension or mobile companion app would extend real-world reach.
- **Batch processing** - currently experimental, with full integration planned for a future release.

## 🎓 Academic Context

Celestial Shield AI was developed as an **Individual Project ** final submission, and has since been presented at academic/research conferences, including **EXITO 2026**.

## 📄 License

This project was developed for academic coursework. Source code is kept private; this repository is intended for documentation and demonstration purposes. All rights reserved unless a `LICENSE` file states otherwise.

## 👤 Author

**Praveen  Perera**
Cybersecurity · Machine Learning · Application Development

---

<div align="center">
<sub>Built to make cybersecurity awareness accessible to everyone — not just the technical few.</sub>
</div>
