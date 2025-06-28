## 📄 1. Requirements (`requirements.md`)

### 🎯 Core Features

* Note management with `.adoc` format
* Task & checklist management (`.json`)
* Appointment management with calendar sync
* Central login with local user file support
* Real-time and manual synchronization
* Offline-first operation
* Strong encryption (AES-256)
* Web, mobile (iOS/Android), and desktop app
* Team comments (optional)
* File attachments (images, PDFs, etc.)
* PWA functionality for web version
* Knowledge database features (tagging, linking, graph view)

### 🛡️ Privacy & Security

* End-to-end encryption for content
* Secure local storage
* OAuth2 for authentication

---

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

---

## 📊 3. Data Model (`data-model.md`)

### 🧩 Entity: `Note`

```json
{
  "id": "note-91a27d",
  "title": "Onboarding Guide",
  "slug": "onboarding-guide",
  "namespace": "Docs/Guides",
  "content": "= Welcome Guide\n\nThis note links to [[Getting Started]].",
  "tags": ["guide", "setup", "team"],
  "attachments": ["file-user-manual.pdf"],
  "created_at": "2025-06-27T10:00:00Z",
  "updated_at": "2025-06-27T12:00:00Z",
  "author": "user-123",
  "linked_note_ids": ["note-57bb45", "note-b321ab"],
  "backlinks": ["note-a8c741"],
  "version": 4,
  "history": [...],
  "encrypted": true,
  "checksum": "b2741a4c8e..."
}
```

### 📂 Related Entities

* `Attachment`
* `TagIndex`
* `GraphCache`

---

## 🔁 4. Sync Concept (`sync-concept.md`)

### 🔄 Sync Strategy

* Hash/Checksum-based delta sync
* Conflict resolution via merge UI or timestamp
* Sync both `.adoc` and `.json` content
* Versioned history stored per note
* Rebuild backlinks dynamically on sync

### 🔐 Encryption

* AES-256-GCM for notes and attachments
* Key stored locally, optionally passphrase-protected
* Transport over TLS + JWT

### 🧪 Example Sync Process

```plaintext
1. Load local cache
2. For each local note:
    a. Compute checksum
    b. Compare with remote
    c. If different, send delta or full
    d. Save new version
3. Rebuild tag/index/graph cache
```

---

## 🚀 5. Roadmap (`roadmap.md`)

### ✅ MVP

* Core UI (Notes, Tasks, Checklists)
* Offline Editing
* GitHub file sync
* Encryption engine
* Calendar read support

### 🔜 Phase 1

* Full calendar CRUD
* Realtime sync (WebSocket)
* Attachments
* Tag & link graph
* PWA full offline support

### 🔮 Phase 2

* Team chat/comments
* User roles & rights
* Full-text search
* Web import/export
* Multi-language support
