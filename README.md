# 🛡️ Celestial Shield AI: Phishing & Smishing Detection System

## 📌 Executive Summary
Phishing and smishing attacks frequently target non-technical users through deceptive language and psychological triggers like urgency or financial incentives. **Celestial Shield AI** is a standalone desktop application developed to detect both email-based phishing and SMS-based smishing messages while actively promoting cybersecurity awareness.

Unlike standard detection tools that output a simple binary result, this system bridges the gap between machine learning research and practical usability. It provides structured risk levels (Low, Medium, High), confidence percentage scores, and color-coded visual indicators to help users understand the exact level of threat.

---

## 🚀 Core Features
*   **Unified Threat Detection:** Analyzes textual patterns in both emails and mobile SMS messages.
*   **Structured Risk Interpretation:** Translates probabilistic model outputs into clear, actionable risk categories rather than forcing absolute decisions.
*   **Visual Confidence Indicators:** Utilizes dynamic, color-coded progress bars to reflect the model's certainty, aiding rapid visual interpretation.
*   **On-Demand Security Reporting:** Generates structured, timestamped TXT reports for personal documentation without automatically saving data.
*   **Privacy-First Architecture:** Operates entirely offline with a session-based memory logging system. User inputs are never permanently stored or transmitted externally.
*   **Real-Time Analytics:** Features a statistical summary tab and session-based scan history for immediate feedback during application runtime.

---

## 📸 System Showcase

**MAIN INTERFACE**
<img width="1917" height="1030" alt="01 Dashboard" src="https://github.com/user-attachments/assets/4955e1fb-50e5-41d3-8dc7-343127e79ef8" />
> *The split-panel dashboard prioritizes readability, separating user input from the classification results and security advisories.*

**HIGH RISK / SMISHING IN DARK MODE'**
<img width="1918" height="1031" alt="02 Smishing" src="https://github.com/user-attachments/assets/ba8ef0e5-a116-4b65-98ce-7e3ffe312576" />
> *Detecting a smishing attempt. The system highlights high-risk threats with a red confidence bar and provides immediate "DO NOT" advisory warnings.*

**HIGH RISK / PHISHING IN DARK MODE'**
<img width="1919" height="1030" alt="03 Phishing" src="https://github.com/user-attachments/assets/618c1b49-c7df-4185-9659-47f293d78bd3" />
> *Detecting a Phishing attempt. The system highlights high-risk threats with a red confidence bar and provides immediate "DO NOT" advisory warnings, identified URLs. & Keywords. *

**MEDIUM RISK / SUSPICIOUS**
<img width="1916" height="1031" alt="06 Suspicious" src="https://github.com/user-attachments/assets/4ab7e58e-e920-4ec2-9976-fad4da37430f" />
> *Evaluating a borderline message. The system assigns a 'Medium' risk level with an orange confidence indicator, advising the user to proceed with caution and verify the source.*

**LOW RISK / SAFE**
<img width="1917" height="1031" alt="05 Safe" src="https://github.com/user-attachments/assets/9fd0e7c1-6ab9-49df-9806-234c08180ac6" />
> *Evaluating a legitimate message. The system assigns a 'Low' risk level with a green confidence indicator, acknowledging the absence of strong threat patterns.*

**BATCH PROCESSING**
![Batch Processing Module](screenshots/batch_processing.png)
> *An experimental enhancement component designed for scalable multi-message analysis, expanding the system's capabilities beyond single-message inputs.*

**STATISTICS**
<img width="1915" height="1027" alt="08 Staticsts " src="https://github.com/user-attachments/assets/ad58851d-539d-4919-90e6-6f263e6a46fd" />
> *The real-time statistical summary component provides immediate feedback on detection activity, displaying model information and a summary of safe versus malicious scans during the session.*

**[📸 INSERT 'REPORT GENERATION' SCREENSHOT HERE]**
![TXT Report Generation](screenshots/report_generation.png)
> *On-demand structured TXT security reports output the timestamp, classification result, and emergency advisory notices relevant to local authorities.*

---

## ⚙️ System Architecture & Technology Stack
The system is designed with a modular architecture, separating preprocessing, feature extraction, classification, and GUI operations.

*   **Programming Language:** Python
*   **User Interface:** Tkinter (Desktop GUI)
*   **Feature Extraction:** Term Frequency Inverse Document Frequency (TF-IDF)
*   **Classification Algorithm:** Logistic Regression

### 🧠 Machine Learning Methodology
The core detection mechanism relies on supervised text classification. TF-IDF vectorization was chosen to measure the importance of words within a message relative to the overall dataset, effectively highlighting significant terms associated with malicious patterns. 

Logistic Regression was utilized to evaluate these numerical features because it produces interpretable probability outputs (confidence scores) and requires low computational resources, making it ideal for a lightweight, offline desktop application.

### 📊 Model Performance Metrics
The model was trained and validated using publicly available datasets containing labeled phishing, smishing, and legitimate messages.
*   **Overall Accuracy:** 93%
*   **Precision (Weighted Avg):** 93%
*   **Recall (Weighted Avg):** 93%
*   **F1-Score (Weighted Avg):** 93%

---

## 💻 Core Logic Snippets

*(Note: The full source code is kept private to protect intellectual property. Below are key logic snippets demonstrating the system's underlying processing pipeline).*

### 1. Text Preprocessing (Noise Reduction)
Before classification, input text is cleaned to ensure consistency. URLs, numbers, and special characters are removed or tokenized.

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
