<div align="center">

# 🩺 Roshta (روشتة)
### AI-Powered Clinical Decision Support Tool for Egyptian Prescriptions

[![Next.js](https://img.shields.io/badge/Next.js-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)](https://flutter.dev/)
[![.NET](https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)

</div>

**Roshta** is an AI-powered web and mobile clinical decision-support platform designed to assist pharmacists in Egypt. The system reads handwritten, code-switched (Arabic/Latin) prescriptions, extracts medication details, checks for dangerous drug-drug interactions, and suggests affordable bioequivalent local generics.

> 🛡️ **Safety First:** Roshta does *not* make autonomous substitutions. It acts as an assistant to the pharmacist, who must review and confirm all AI predictions before dispensing.

---

## 📖 Table of Contents
1. [Core Problem Addressed](#-core-problem-addressed)
2. [Key Features](#-key-features)
3. [System Architecture](#️-system-architecture)
4. [Repository Structure](#-repository-structure)
5. [Getting Started (Local Development)](#-getting-started-local-development)
6. [Data Sources & AI Models](#-data-sources--ai-models)
7. [Documentation](#-project-documentation)
8. [The Team](#-the-team-team-synapse)

---

## 📌 Core Problem Addressed
1. **Technical Gap:** Standard OCR engines (like Tesseract) fail on cursive, non-standardized, mixed Arabic/Latin handwriting.
2. **Safety Gap:** Pharmacists struggle to manually remember every dangerous drug-drug interaction.
3. **Economic Gap:** Patients overpay for imported brands when identical, cheaper local generics exist but are underused.

---

## ✨ Key Features
*   **Dual-Mode Operation:** 
    *   📸 *Prescription Mode:* Capture, OCR, NER extraction, and Human-in-the-loop verification.
    *   🔍 *Search Mode (P1):* Fast drug lookup and interaction checking for walk-in patients.
*   **🧠 AI Pipeline:** Layout Segmentation (PaddleOCR) → Handwriting Recognition (TrOCR) → Entity Extraction (NER) → Fuzzy Matching.
*   **🛑 Safety Gate (Liability Checkbox):** If a Major drug interaction is detected via the **SafeRx API**, the system blocks confirmation until the user checks a mandatory liability checkbox (logged in the Audit Trail).
*   **🌍 Bilingual UI:** Full English and Arabic (RTL) support with standard medical fonts.
*   **🔒 Privacy Compliant:** Zero storage of patient medical histories or personal identifiers (PDPL 151/2020 compliant).

---

## 🛠️ System Architecture
The platform uses a microservice architecture acting as an API Gateway.

<!-- Add your draw.io architecture image here -->
<div align="center">
  <i>(Insert System Architecture Diagram Here)</i>
</div>

1. **Client Layer:** 
   *   **Web:** Next.js (Responsive, RTL support)
   *   **Mobile:** Flutter (First-class pharmacist tool)
2. **Backend API (.NET):** Handles Auth (JWT), Prescription storage, User Management, SafeRx integration, and Audit Logging.
3. **AI Microservice (Python FastAPI):** Internal service (API Key protected) handling TrOCR, NER, and Fuzzy Matching.
4. **Database:** PostgreSQL (Hosted on Render).

🚀 Getting Started (Local Development)
📋 Prerequisites
Node.js (v18+) & npm

Flutter SDK (v3+)

.NET 8 SDK

Python (3.10+)

PostgreSQL (or SQL Server)

1. ⚙️ Backend (.NET)
bash
cd backend
# Update appsettings.json with your local database connection string
dotnet restore
dotnet ef database update
dotnet run
2. 🤖 AI Microservice (Python)
bash
cd ai-service
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
3. 💻 Web Frontend (Next.js)
bash
cd web
npm install
npm run dev
4. 📱 Mobile App (Flutter)
bash
cd mobile
flutter pub get
flutter run
📊 Data Sources & AI Models
Drug Registry: 25,000+ Egyptian medications imported from open-source GitHub datasets (Eg-drugs).

Interaction Screening: Integrated with the SafeRx API.

AI Models:

microsoft/trocr-base-handwritten (Fine-tuned on Egyptian data)

Arabic/Medical NER language model.

Fuzzy string matching (RapidFuzz).

📋 Project Documentation
All detailed academic and technical documents are located in the /docs folder:

📄 Software Requirements Specification (SRS)

🗺️ Entity Relationship Diagram (ERD)

🔗 REST API Specification (Swagger)

🏗️ System Design Document

👥 The Team (Team Synapse)
Faculty of Computers and Information — Graduation Project 2027

Role	Team Members
Team Lead	Semon Hany
Backend (.NET)	Abear Atef, Mohamed Hamdon, Marcos Adel
Frontend (Next.js)	Aya Sayed, Eman Ahmed, Manar Abead
Mobile (Flutter)	Mohamed Erian, Semon Hany
AI & Data (Python)	Mostafa Mohamed
UI/UX Designer	Aya AbdElrahem
⚠️ Disclaimer
This project was developed as an academic graduation project. The AI models and interaction screening tools provided are for clinical decision support only. They do not replace the professional judgment of a licensed pharmacist. Always verify drug interactions and substitutions against official medical references.

<div align="center"> <i>Built with ❤️ by Team Synapse</i> </div> ```
