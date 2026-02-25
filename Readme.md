Below is a **complete, professional `README.md`** tailored exactly to the system you built — no extra features added, no exaggeration, clean technical structure.

You can directly paste this into your GitHub repository.

---

# AI-Driven DDoS Detection & Mitigation System

## Overview

This project presents a real-time AI-assisted system for detecting and mitigating DoS/DDoS attacks in virtualized network environments. The system was implemented and validated in an SDN/NFV setup using open-source tools. It combines machine learning–based anomaly detection with adaptive thresholding and automated mitigation.

The primary objective is to accurately distinguish between benign and malicious traffic under dynamic network conditions and respond automatically without human intervention.

---

## Key Features

* Real-time network traffic monitoring
* Adaptive threshold-based anomaly pre-check
* Supervised machine learning classification (XGBoost)
* Automated mitigation using iptables rules
* Cloud-hosted inference via lightweight API
* Low false positive rate
* Autonomous operation without manual response

---

## System Architecture

The system operates as a closed-loop detection and mitigation pipeline:

```
Live Traffic Monitoring
        ↓
Feature Extraction
        ↓
AI-Based Classification (XGBoost)
        ↓
Automated Mitigation (iptables)
```

### Components

1. **Network Environment**

   * Implemented using Mininet
   * Emulates SDN/NFV-based topology
   * Hosts generate benign and attack traffic

2. **Traffic Monitoring**

   * Real-time packet sniffing
   * Per-source IP traffic aggregation
   * Feature extraction from live packets

3. **Adaptive Threshold Mechanism**

   * Dynamically adjusts detection sensitivity
   * Based on live packet rate and SYN packet rate
   * Reduces false positives during traffic bursts

4. **Machine Learning Model**

   * Supervised XGBoost classifier
   * Trained using reduced NSL-KDD dataset
   * Binary classification:

     * Normal
     * Anomaly (DoS/DDoS)

5. **Model Deployment**

   * Hosted remotely (cloud-based environment)
   * Accessed via REST API
   * Near real-time inference

6. **Automated Mitigation**

   * Detected malicious source IP is blocked
   * Implemented using iptables
   * Blocking duration is controlled and temporary
   * Expired rules are automatically removed

---

## Dataset

* Dataset Used: **NSL-KDD**
* Focused classes:

  * Benign traffic
  * DoS/DDoS traffic
* Feature reduction applied (from 42 to 15 features)
* Dataset split:

  * 80% training
  * 20% testing

---

## Model Performance

| Metric          | Result    |
| --------------- | --------- |
| Accuracy        | 99.98%    |
| Precision       | ~99.98%   |
| Recall          | ~99.98%   |
| F1-Score        | ~99.98%   |
| False Positives | Near Zero |

The system successfully detected and mitigated high-volume DDoS traffic during live testing using Hping.

---

## Deployment Flexibility

Although validated in an SDN/NFV environment, the detection pipeline is deployment-agnostic. The AI classification layer can be adapted for:

* Traditional enterprise networks
* Cloud infrastructures
* Hybrid network setups
* Monitoring platforms

Only the mitigation mechanism needs to be adjusted to match the target environment.

---

## License

This project is developed for academic and research purposes.

---

This project demonstrates a practical AI-driven approach to real-time DDoS detection and mitigation in virtualized environments. It serves as a functional proof of concept and can be extended or customized based on organizational requirements.

