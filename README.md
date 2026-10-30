# 🩺 Roshta (روشتة)
### AI-Powered Clinical Decision Support Tool for Egyptian Prescriptions

[![Next.js](https://img.shields.io/badge/Next.js-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)](https://flutter.dev/)
[![.NET](https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)

**Roshta** is an AI-powered web and mobile clinical decision-support platform designed to assist pharmacists in Egypt. The system reads handwritten, code-switched (Arabic/Latin) prescriptions, extracts medication details, checks for dangerous drug-drug interactions, and suggests affordable bioequivalent local generics.

> **Safety First:** Roshta does *not* make autonomous substitutions. It acts as an assistant to the pharmacist, who must review and confirm all AI predictions before dispensing.

---

## 📌 Core Problem Addressed
1. **Technical Gap:** Standard OCR engines (like Tesseract) fail on cursive, non-standardized, mixed Arabic/Latin handwriting.
2. **Safety Gap:** Pharmacists struggle to manually remember every dangerous drug-drug interaction.
3. **Economic Gap:** Patients overpay for imported brands when identical, cheaper local generics exist but are underused.

---

## ✨ Key Features
*   **Dual-Mode Operation:** 
    *   *Prescription Mode:* Capture, OCR, NER extraction, and Human-in-the-loop verification.
    *   *Search Mode (P1):* Fast drug lookup and interaction checking for walk-in patients.
*   **AI Pipeline:** Layout Segmentation (PaddleOCR) → Handwriting Recognition (TrOCR) → Entity Extraction (NER) → Fuzzy Matching.
*   **Safety Gate (Liability Checkbox):** If a Major drug interaction is detected via the **SafeRx API**, the system blocks confirmation until the user checks a mandatory liability checkbox (logged in the Audit Trail).
*   **Bilingual UI:** Full English and Arabic (RTL) support with standard medical fonts.
*   **Privacy Compliant:** Zero storage of patient medical histories or personal identifiers (PDPL 151/2020 compliant).

---

## 🛠️ System Architecture
The platform uses a microservice architecture acting as an API Gateway:

1. **Client Layer:** 
   *   **Web:** Next.js (Responsive, RTL support)
   *   **Mobile:** Flutter (First-class pharmacist tool)
2. **Backend API (.NET):** Handles Auth (JWT), Prescription storage, User Management, SafeRx integration, and Audit Logging.
3. **AI Microservice (Python FastAPI):** Internal service (API Key protected) handling TrOCR, NER, and Fuzzy Matching.
4. **Database:** SQL Server.

---

## 📂 Repository Structure
```text
├── /web              # Next.js frontend application
├── /mobile           # Flutter mobile application
├── /backend          # .NET Core REST API
├── /ai-service       # Python FastAPI AI Microservice
├── /docs             # SRS, ERD, API Specifications (OpenAPI/Swagger)
└── README.md
