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