# SHACDSS
# 🏥 Smart Hospital Appointment and Clinical Decision Support System (SHACDSS)

[![CUK Compliance](https://img.shields.io/badge/CUK_SCM-2024_Guidelines-blue?style=flat-square)](https://www.cuk.ac.ke/)
[![API Integration](https://img.shields.io/badge/Mandatory_API-Gava_Connect_%26_Daraja_3-green?style=flat-square)](#)
[![License](https://img.shields.io/badge/license-MIT-red.svg?style=flat-square)](LICENSE)

**SHACDSS** is an AI-powered healthcare management platform designed to optimize outpatient workflows in Kenyan hospitals. By bridging the gap between administrative scheduling and preliminary clinical assessment, the system mitigates facility congestion and provides healthcare providers with data-driven insights prior to consultation.

---

## 📋 Table of Contents
- [Overview](#-overview)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Mandatory API Integrations](#-mandatory-api-integrations)
- [Machine Learning Engine](#-machine-learning-engine)
- [Technologies Used](#-technologies-used)
- [Installation & Setup](#-installation--setup)
- [API Documentation](#-api-documentation)
- [Ethical & Safety Constraints](#-ethical--safety-constraints)
- [Acknowledgements](#-acknowledgements)

---

## 🌟 Overview
Healthcare facilities in Kenya currently face significant challenges including severe outpatient congestion, long physical queues, and fragmented patient records. **SHACDSS** will address these issues by providing a unified digital platform for:
1. **Asynchronous Scheduling**: Transitioning from physical queues to digital time-slots.
2. **Clinical Decision Support**: Utilizing Machine Learning to provide clinicians with preliminary symptom assessments.
3. **National Integration**: Implementing mandatory government-aligned APIs for identity and payments.

---

## ✨ Key Features
- **Verified Identity (Gava Connect)**: Secure login for patients and clinicians using verified national digital IDs.
- **Cashless Payments (Daraja 3)**: Integrated M-Pesa gateway for processing hospital consultation fees during booking.
- **Smart Triage Engine**: A Random Forest-based classifier that analyzes patient symptoms and suggests probable conditions.
- **Urgency Flagging**: Automated prioritization of patients based on symptom severity.
- **Clinician Dashboard**: A "Human-in-the-loop" interface allowing doctors to review pre-assessment summaries before consultation.
- **Unified Electronic Health Records (EHR)**: Secure, centralized storage for patient history and consultation notes.

---

## 🏗 System Architecture
The system will follow a robust **3-tier architecture** to ensure scalability and security:

| Layer | Component | Description |
|:--- |:--- |:--- |
| **Presentation** | React / Flutter | User interface for patients (mobile/web) and clinicians. |
| **Application** | Django (Python) | Business logic, ML model serving, and API orchestration. |
| **Data Layer** | PostgreSQL | Secure relational database for patient and transaction records. |

---

## 🔑 Mandatory API Integrations

### 1. Gava Connect API (Identity Management)
* **Function:** Used as the primary Authentication Provider. 
* **Implementation:** Patients and Clinicians will verify their accounts using their national digital ID, ensuring that medical records are legally and accurately tied to the correct individual.

### 2. Daraja 3 API (M-Pesa Payments)
* **Function:** Financial Transaction Gateway.
* **Implementation:** The system triggers an **M-Pesa STK Push** during the appointment booking process. A booking is only confirmed upon successful callback from the Daraja API, ensuring a 100% cashless administrative workflow.

---

## 📊 Machine Learning Engine
The core of the system is a **Random Forest Classifier** trained on validated clinical datasets. Unlike simple rule-based systems, this model will evaluate multiple symptom vectors to provide a probabilistic suggestion.

### Why Random Forest?
- **Resistance to Overfitting**: Handles high-dimensional symptom data effectively.
- **Interpretability**: Allows for feature importance analysis (identifying which symptoms are most critical).
- **Scalability**: Can be updated iteratively with new clinical data.

---

## 🛠 Technologies Used
- **Backend**: Python (Django Framework)
- **Frontend**: React.js / Flutter
- **Database**: PostgreSQL
- **Machine Learning**: Scikit-learn (Random Forest Classifier), Pandas, NumPy
- **Authentication**: Gava Connect API
- **Payments**: Daraja 3 API (M-Pesa)
- **Deployment**: Docker / Gunicorn

---

## 🚀 Installation & Setup

### Prerequisites
- Python 3.9+
- Node.js (for React frontend)
- PostgreSQL
- M-Pesa Developer Credentials (Safaricom Daraja)

<!--  ### Local Environment Setup
1. **Clone the Repository**:
   ```bash
   git clone [https://github.com/Motondi/SHACDSS.git](https://github.com/Motondi/SHACDSS.git)
   cd SHACDSS 
   
    Backend Configuration:
      cd backend
      pip install -r requirements.txt
      python manage.py migrate
      python manage.py runserver

    Frontend Configuration:
      cd frontend
      npm install
      npm start
   
   -->

---

## 📚 API Documentation
Endpoint,                     Method,                     Description
/api/auth/gava/,            POST,                       Authenticates user via Gava Connect identity token.
/api/pay/stk-push/,         POST,                       Initiates Daraja 3 M-Pesa STK Push for consultation fees.
/api/predict/symptoms/,     POST,                       Submits symptoms to the ML model for clinical suggestion.
/api/appointments/,         GET/POST,                   Manages scheduling slots and booking confirmations.

---

## ⚖️ Ethical & Safety Constraints
Non-Diagnostic Clause: The system is an assistive tool (Decision Support) and will not issue final medical diagnoses.

Human-in-the-loop: All system outputs must be verified and signed off by a licensed medical professional.

Data Privacy: All sensitive patient data is encrypted and managed through strict Role-Based Access Control (RBAC).

---

## 🙏 Acknowledgements
The Co-operative University of Kenya (CUK): School of Computing and Mathematics (SCM).

Safaricom PLC: For the Daraja 3 API framework.

Gava Connect: For the national identity management gateway.

---
