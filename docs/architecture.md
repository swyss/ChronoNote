## 🧱 2. Architecture (`architecture.md`)

### 🔧 System Components

* **Mobile App**: Flutter
* **Desktop App**: Electron + Quasar
* **Web App**: Quasar PWA
* **Backend**:

  * Sync API Gateway (Node/Go/Python)
  * Calendar API Layer (Google/Outlook)
  * GitHub storage proxy

### 🧭 Data Formats

* Notes: `.adoc`
* Tasks: `.json`
* Checklists: `.json`
* Attachments: Binary (AES-encrypted)
* Calendar: Google Calendar API, Outlook Graph API

### 📦 Folder Structure

```bash
project-root/
├── apps/
│   ├── mobile/         # Flutter App
│   ├── desktop/        # Electron + Quasar
│   └── web/            # PWA
├── backend/
│   ├── api-gateway/
│   ├── auth-service/
│   ├── sync-service/
│   ├── calendar-service/
│   └── encryption/
├── shared/
│   ├── models/
│   ├── utils/
│   └── config/
├── docs/
│   ├── requirements.md
│   ├── architecture.md
│   ├── data-model.md
│   ├── sync-concept.md
│   └── roadmap.md
└── .github/
    └── workflows/
```