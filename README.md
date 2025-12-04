

# **DD-Beta Simulator**

### *Behavioral Pattern Generator & Anomaly Detection Testbed for Dementia Research*

DD-Beta is a **custom web-based simulator** used for testing early-stage dementia detection models.
It generates **daily mobility patterns**, injects **controlled anomalies**, and evaluates **AI-based anomaly detection algorithms** in real time.

This tool was created to support the thesis project:
**“AI-Powered Dementia Early Detection System using GPS-based Behavioral Analysis.”**

---

## 🔍 **Purpose of DD-Beta**

DD-Beta was developed because using real patient mobility data is:

* ethically difficult,
* slow to collect, and
* hard to reproduce.

This simulator allows safe, fast, and repeatable experiments without any sensitive personal data.

---

## ✨ **Key Features**

* **Baseline Route Generation**
  Creates realistic daily routines (Home → Store → Park → Home), including small natural GPS noise.

* **Learning Simulation**
  Models a 0–100% “learning progress” similar to an AI learning a user's normal behavior.

* **Anomaly Injection**
  Adds different types of abnormal behavior, such as:

  * wandering
  * taking a wrong route
  * missing expected locations
  * time-of-day irregularities

* **Real-Time Anomaly Detection**
  Calculates reconstruction error and anomaly score for each point.

* **Visualizations**

  * Real-time map
  * Error charts
  * Learning progress
  * Anomaly markers

* **Threshold Calibration Tools**
  Supports fixed and adaptive thresholding (mean + 3σ).

---

## 📌 **Why DD-Beta Matters**

DD-Beta makes it possible to:

* test anomaly detection **without real patients**,
* evaluate different AI models quickly,
* compare baseline vs anomaly patterns visually,
* detect weaknesses such as **overfitting** at high learning percentages,
* prepare for real-world Android deployment.

DD-Beta acts as a “sandbox” to tune the AI model before integrating it into the Android app.

---

## 🧠 **AI Model Used (Simulator Version)**

The simulator uses **TensorFlow.js** to run an **autoencoder** directly in the browser.

**Autoencoder Structure:**

* Input layer: GPS + time features
* Encoder: Dense(32) → Dense(16)
* Decoder: Dense(32) → Output(40)
* Output error: Mean Squared Error (MSE)

The model learns “normal” behavior and produces high error when detecting unusual movement.

---

## ⚠️ **Known Issues**

### **1. Overfitting at 100% Learning Progress**

When learning reaches 100%, the model becomes too strict.
Even very small noise becomes an anomaly.

→ **Solution:** adaptive thresholds, memory decay, moving window.

### **2. No Forgetting Mechanism**

Old patterns remain forever, which is unrealistic.

→ **Planned Fix:** exponential decay of old data.

### **3. GPS Noise Sensitivity**

Small changes in coordinates may inflate error.

→ **Planned Fix:** data smoothing or clustering.

---

## ▶️ **How to Use**

### **1. Open the simulator**

```text
https://hexia7230.github.io/DD-Beta/
```

### **2. Choose your options**

* Number of days
* Noise level
* Learning percentage
* Anomaly type (wandering, wrong route, missing stop, etc.)

### **3. Run Simulation**

Press “Start Simulation.”

### **4. Analyze Results**

You can view:

* Map movement
* Error chart
* Anomaly count
* Learning progress
* Anomaly threshold

---

## 📁 **Project Structure**

```
index.html       → Main interface and layout
style.css        → Styling and UI themes
script.js        → Core simulation logic
model.js         → TensorFlow.js model (autoencoder)
utils.js         → GPS noise, anomaly generation, helpers
assets/          → Icons, fonts, images
```

---

## 🛠️ **Technologies Used**

* **JavaScript**
* **TensorFlow.js**
* **Leaflet.js (for the map)**
* **Chart.js (for graphs)**
* HTML/CSS

---

## 🚀 **Roadmap / Future Work**

* Add LSTM model for sequence analysis
* Add dynamic time-warping comparison
* Implement memory decay and moving windows
* Create exportable datasets for Android training
* Build “DD-Beta Pro” for research labs
* Integrate real GPS sampling from Android app

---

## 📜 **License**

MIT License.
Free to use, modify, and share for academic and personal projects.

---

## 👤 **Author**

**Terashita Sho**
Bachelor of Science in Information Technology
Southville International School and Colleges

GitHub: *[https://github.com/hexia7230](https://github.com/hexia7230)*

---


Just say **“add badges”** or **“add screenshots”**.
