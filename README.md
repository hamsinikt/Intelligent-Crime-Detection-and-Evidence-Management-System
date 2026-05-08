Intelligent-Crime-Detection-and-Evidence-Management-System
The Intelligent Crime Detection and Evidence Management System uses AI to detect suspicious activities in real time. It automatically records and stores incidents with time and location as digital evidence. This improves public safety by enabling faster and more reliable crime response
# Product Specification Document (PSD)

## Intelligent Crime Detection and Evidence Management System (ICDEMS)

---

### 1. Product Overview

**Product Name:** Intelligent Crime Detection and Evidence Management System (ICDEMS)

**Product Type:** Embedded IoT System with AI/ML Integration

**Target User:** Law Enforcement Agencies, Forensic Labs, Police Departments

**Project Level:** Undergraduate ECE Engineering Capstone

---

### 2. Problem Statement

Conventional crime scene investigation relies on manual evidence collection, human-dependent surveillance analysis, and fragmented digital record-keeping. This leads to evidence tampering, delayed case resolution, chain-of-custody gaps, and human error in pattern detection.

---

### 3. Product Objectives

| # | Objective | Measurable Outcome |
|---|-----------|-------------------|
| 1 | Automate evidence capture and cataloging | 90% reduction in manual evidence logging |
| 2 | Real-time suspicious activity detection | < 2 second alert latency |
| 3 | Immutable evidence chain-of-custody | Forensic audit trail with tamper-proof timestamps |
| 4 | Centralized evidence repository | All case data accessible from single dashboard |
| 5 | Facial/suspect recognition | > 85% accuracy on custom dataset |

---

### 4. System Architecture

```
┌──────────────────────────────────────────────────┐
│                   USER LAYER                      │
│    Web Dashboard   │   Mobile App   │   API        │
└──────────────────────┬───────────────────────────┘
                       │
┌──────────────────────▼───────────────────────────┐
│                 APPLICATION LAYER                  │
│    Flask/FastAPI Server   │   AI Inference Engine │
│    DB Interface           │   Alert Manager       │
└──────────────────────┬───────────────────────────┘
                       │
┌──────────────────────▼───────────────────────────┐
│                   DATA LAYER                      │
│  PostgreSQL │  Local Storage │  Blockchain Hash   │
└──────────────────────┬───────────────────────────┘
                       │
┌──────────────────────▼───────────────────────────┐
│                 HARDWARE LAYER                     │
│  Cameras │ Sensors │ GPS │ RFID │ Biometrics      │
└──────────────────────────────────────────────────┘
```

---

### 5. Hardware Specifications (ECE Core)

#### 5.1 Edge Processing Unit

| Component | Specification | Purpose |
|-----------|--------------|---------|
| **SoC** | Raspberry Pi 4 (4GB) / Jetson Nano | AI inference at edge |
| **Camera Module** | Raspberry Pi Camera v2 (8MP / 1080p) / USB Webcam | Video feed capture |
| **GPS Module** | NEO-6M / u-blox NEO-M8N | Crime location geotagging |
| **Motion Sensor** | PIR HC-SR501 | Trigger-based recording |
| **RFID Scanner** | MFRC522 | Evidence tag reading/writing |
| **Fingerprint Sensor** | R307 Optical | Officer authentication |
| **Storage** | 128GB SD Card + 1TB External HDD | Evidence archival |
| **Display** | 7" TFT Touchscreen (optional) | On-site evidence review |
| **Power** | 5V/3A DC Adapter + 10,000mAh Power Bank | Portable operation |
| **Communication** | Wi-Fi (built-in) + GSM SIM800L (backup) | Network uplink |

#### 5.2 Additional Sensors (Optional Expansions)

- **Temperature/Humidity** (DHT22) — environmental condition logging
- **Gas Sensor** (MQ-2/MQ-135) — arson/chemical detection
- **Vibration Sensor** (SW-420) — forced entry detection
- **Ultrasonic** (HC-SR04) — proximity/object dimension logging

#### 5.3 Hardware Block Diagram

```
         ┌──────────────┐
         │  Camera(s)   │────┐
         └──────────────┘    │
         ┌──────────────┐    │    ┌─────────────────┐     ┌─────────────┐
         │  PIR Sensor  │────┤    │                 │     │  Cloud/DB   │
         └──────────────┘    ├────►  Raspberry Pi 4 ├────►│             │
         ┌──────────────┐    │    │  / Jetson Nano  │     └─────────────┘
         │  GPS Module  │────┤    │                 │
         └──────────────┘    │    └────────┬────────┘
         ┌──────────────┐    │             │
         │ RFID Scanner │────┘    ┌────────▼────────┐
         └──────────────┘         │  Touchscreen    │
         ┌──────────────┐         │  Display (7")   │
         │ Fingerprint  │────────>│                 │
         └──────────────┘         └─────────────────┘
```

---

### 6. Software Specifications

#### 6.1 Technology Stack

| Layer | Technology | Version |
|-------|-----------|---------|
| **OS** | Raspberry Pi OS (Lite) / Ubuntu | 22.04 LTS |
| **Backend API** | Python Flask / FastAPI | 3.10+ |
| **AI/ML** | TensorFlow Lite / OpenCV / YOLOv8 | Latest |
| **Database** | PostgreSQL + SQLite (local) | 15 |
| **Frontend** | React.js / Streamlit | Latest |
| **Blockchain** | SHA-256 Hash Chain (custom) | — |
| **Protocol** | MQTT + HTTP REST | — |
| **Container** | Docker (optional) | Latest |

#### 6.2 AI/ML Models

| Model | Task | Framework |
|-------|------|-----------|
| YOLOv8n | Object detection (weapons, tools) | Ultralytics |
| FaceNet / Face Recognition | Suspect identification | dlib / OpenCV |
| OpenPose / MediaPipe | Suspicious human pose detection | TensorFlow |
| Custom CNN | Fire/gunshot audio detection | TensorFlow |
| LSTM | Anomaly behavior prediction | Keras |

---

### 7. Functional Requirements

#### 7.1 Core Features (Mandatory)

| FR-ID | Feature | Description |
|-------|---------|-------------|
| FR-01 | Live Video Surveillance | Real-time camera feed with motion-triggered recording |
| FR-02 | Suspicious Activity Detection | AI detects weapons, fights, trespassing, unusual behavior |
| FR-03 | Evidence Tagging | RFID/NFC tag assignment to physical evidence with timestamp |
| FR-04 | Chain of Custody | Digital log: who accessed evidence, when, and why |
| FR-05 | Case Dashboard | Web-based UI to view cases, evidence, and analytics |
| FR-06 | Alert System | SMS/Email/Push notification on threat detection |
| FR-07 | Geotagging | GPS coordinates attached to every evidence item |
| FR-08 | User Authentication | Role-based access (Officer, Investigator, Admin) with biometric |

#### 7.2 Advanced Features (Optional)

| FR-ID | Feature | Description |
|-------|---------|-------------|
| FR-09 | Audio Gunshot Detection | Microphone array + ML classification |
| FR-10 | Tamper Detection | Evidence hash verification detects alteration |
| FR-11 | Heatmap Generation | Crime hotspot visualization over map |
| FR-12 | Report Generation | Auto-generate PDF case reports |
| FR-13 | Blockchain Ledger | Distributed evidence integrity verification |

---

### 8. Non-Functional Requirements

| NFR-ID | Requirement | Target |
|--------|-------------|--------|
| NFR-01 | Detection Latency | < 3 seconds from event to alert |
| NFR-02 | System Uptime | > 99% (excluding scheduled maintenance) |
| NFR-03 | Evidence Storage | Minimum 10,000 evidence records |
| NFR-04 | Video Storage | 7-day rolling retention at 1080p |
| NFR-05 | User Capacity | Support 50+ concurrent users |
| NFR-06 | Security | AES-256 encryption at rest & in transit |
| NFR-07 | Power Backup | Minimum 4 hours on battery |
| NFR-08 | Model Accuracy | > 80% precision, > 75% recall |

---

### 9. Data Flow

#### 9.1 Evidence Lifecycle

```
Collection → Tagging → Encryption → Storage → Hashing → Access Log
   │           │           │           │          │           │
   ▼           ▼           ▼           ▼          ▼           ▼
  Camera   RFID Tag    AES-256    Postgres   SHA-256    Blockchain
  Capture  Attached    Encrypted  DB Store   Hash       Entry
```

#### 9.2 Detection Pipeline

```
Camera Frame → Preprocessing → YOLOv8 Inference → Class Filter
                                                      │
                                              ┌───────┴───────┐
                                              ▼               ▼
                                           Threat (gun)   Non-threat
                                              │               │
                                              ▼               ▼
                                         Alert + Record    Discard
```

---

### 10. User Interface Specifications

#### 10.1 Web Dashboard Pages

| Page | Content |
|------|---------|
| Login | Biometric + password authentication |
| Live Feed | Grid of active camera streams |
| Cases | List of cases with status, date, location |
| Case Detail | Evidence items, timeline, chain-of-custody log |
| Analytics | Crime heatmap, statistics, detection logs |
| Reports | Generate and download PDF/CSV reports |
| Admin Panel | User management, system config, logs |

#### 10.2 Mobile App (Optional)

- Real-time alert notifications
- Quick evidence photo capture
- GPS location tagging
- QR/RFID evidence scanning

---

### 11. Communication Protocols

| Interface | Protocol | Data |
|-----------|----------|------|
| Camera → Pi | CSI / USB | Video stream (H.264) |
| Sensors → Pi | GPIO / I2C / SPI | Sensor readings |
| Pi → Server | MQTT (IoT) / HTTP REST | Evidence data, alerts |
| Server → Client | WebSocket (real-time) / REST | Dashboard data |
| DB → Backup | Cron + rsync | Database dumps |

---

### 12. Implementation Timeline (16 Weeks)

| Phase | Weeks | Deliverable |
|-------|-------|-------------|
| **P1: Research** | 1–2 | Literature survey, component selection |
| **P2: Hardware Assembly** | 3–5 | Circuit connections, sensor integration, camera setup |
| **P3: Base Software** | 4–7 | Flask/FastAPI server, database schema, MQTT setup |
| **P4: AI Model Training** | 6–10 | Dataset collection, YOLOv8 training, model optimization |
| **P5: Integration** | 9–12 | Hardware + software integration, pipeline testing |
| **P6: Dashboard UI** | 10–13 | React/Streamlit frontend, visualization |
| **P7: Testing** | 12–15 | Unit tests, field testing, accuracy evaluation |
| **P8: Documentation** | 14–16 | Final report, user manual, demo video |

---

### 13. Budget Estimate

| Component | Estimated Cost (USD) |
|-----------|---------------------|
| Raspberry Pi 4 (4GB) | $55 |
| Camera Module v2 | $25 |
| PIR + GPS + RFID + Fingerprint | $30 |
| Sensors bundle | $15 |
| SD Card + Power Bank | $25 |
| Miscellaneous (wires, case, etc.) | $20 |
| **Total (hardware)** | **~$170** |

---

### 14. Testing & Validation

| Test Type | Method | Success Criteria |
|-----------|--------|-----------------|
| Detection Accuracy | Confusion matrix on test dataset | Precision > 80% |
| Latency | End-to-end timestamp logging | < 3 seconds |
| Chain of Custody | Simulate evidence handover | All entries recorded |
| Battery Life | Discharge test | > 4 hours |
| Network Failure | Disconnect Wi-Fi | Local buffer, auto-sync |
| Stress Test | 10 simultaneous cameras | No frame drop > 5% |

---

### 15. Future Scope

- Drone integration for aerial crime scene mapping
- License plate recognition (ANPR)
- Voice command evidence logging
- Multi-site distributed deployment
- Court-admissible digital evidence format standardization

---

### 16. References

- YOLOv8: Ultralytics (https://github.com/ultralytics/ultralytics)
- Raspberry Pi Documentation (https://www.raspberrypi.com/documentation/)
- OpenCV: Real-time Computer Vision Library
- NIST Guidelines on Digital Evidence Management

---

**Document Version:** 1.0  
**Prepared For:** ECE Engineering Capstone Project  
**Last Updated:** May 2026
