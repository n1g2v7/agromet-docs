# Transfer Mechanisms

## 1. Google Drive API

### Overview

* Used by: ON1, ON3, AB1, AB2 (partial), SK1 (manual data)
* Fully scripted upload and download

### Workflow

```
Site → Local "files" folder → Google Drive (API upload)
     → Lab download script → Local staging → Processing
```

### Implementation Details

Authentication via service account (`wagner-riddle-auth.json`)

Upload:

* files copied into local `files/` directory
* uploaded using Drive API (`files().create`)

Download:

* list files using `files().list()`
* download via `MediaIoBaseDownload`

Cleanup:

* delete from Drive after successful processing

Acts as **temporary staging**, not long-term storage

## 2. Dropbox Sync

### Overview

* Used by: SK1 (tower + TGA)
* Passive synchronization (no upload script)

### Workflow

```
Site Dropbox folder → Cloud sync → Lab Dropbox folder → Processing
```

### Implementation Details

Site computer:

* Dropbox client monitors directories
* automatic upload (no scripting)

Lab computer:

* Dropbox syncs files locally

Differences from API:

  * no explicit upload/download control
  * timing depends on sync completion
  * no automatic deletion after processing

## 3. DriveHQ / FTP-style Transfer

### Overview

* Used by: AB2 (tower data)
* External cloud/FTP-style system

### Workflow

```
Site → DriveHQ upload → Lab retrieval script → Processing
```

### Implementation Details

Upload handled externally (not in current scripts)

Lab side:
* scheduled retrieval/download

Differences:

* separate authentication system
* less integrated with pipeline
* typically used for tower datasets

## 4. Site Comparison Table

| Site | Tower Data                 | TGA Data   | Manual / Heights | Method Type |
| ---- | --------------------------- | ---------- | ----------------- | ----------- |
| ON1  | Google API                 | Google API | Google API         | Fully API   |
| ON3  | Google API                 | Google API | Google API         | Fully API   |
| SK1  | Dropbox                    | Dropbox    | Google API         | Hybrid      |
| AB1  | External / local + scripts | Google API | Google API         | Hybrid      |
| AB2  | DriveHQ                    | Google API | Google API         | Hybrid      |

!!! note ""Manual / Heights" column"
    This column refers to periodic manual-measurement files: canopy height records,
    leaf area index (LAI) measurements, crop management logs, and other non-automated
    field observations that are uploaded on an irregular schedule (typically after each
    field visit) alongside the continuous automated data. At most sites these files are
    uploaded via the Google Drive API regardless of which mechanism handles the
    high-frequency tower data.

For per-site walkthroughs, see **[Site Implementations](site-implementations.md)**.

