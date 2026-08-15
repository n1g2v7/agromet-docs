# Transfer Architecture & Workflow

## Overview

This page describes how field data are transferred from site computers to the lab processing system across all CanN2Onet sites.

While transfer mechanisms vary (Google Drive API, Dropbox, DriveHQ), all sites follow a common logical workflow:

```
Site Computer → Transfer Mechanism → Lab Staging → Unpack/Organize → Archive → Processing
```

For the exact scheduled times at which each transfer step fires on the lab processing computer, see **[Daily Automation & Task Scheduler](../automation_task_scheduler.md)**.

## 1. Data Transfer Architecture

Different sites use different transfer mechanisms depending on:

* field connectivity
* infrastructure constraints
* historical implementation

### Supported Transfer Mechanisms

* Google Drive API (scripted upload/download)
* Dropbox synchronization (passive sync)
* DriveHQ / FTP-style cloud services
* Hybrid approaches

### Key Design Principles

* Data ingestion is separated from processing
* Transfer is fault-tolerant and restartable
* Files are archived after transfer
* Temporary staging is used before processing

## 2. Common Workflow (Pseudocode)

```text
ALGORITHM DATA_TRANSFER_WORKFLOW

INPUT:
    site-generated data files (tower, TGA, manual)
    transfer mechanism (API / Dropbox / DriveHQ)

OUTPUT:
    organized data in lab repository
    archived transfer files

BEGIN

1. DETECT new data files
    - via API listing, folder scan, or sync client

2. TRANSFER to lab staging
    - download or sync into local staging directory

3. FOR each transferred file:

    IF file is compressed (ZIP):
        copy to temporary directory
        unzip into destination folder

    DETERMINE destination based on:
        - data type (TGA, EC, manual, etc.)
        - site configuration
        - date extracted from filename

    COPY data to:
        (a) main repository
        (b) site mirror directory (if applicable)

    IF file requires conversion (e.g., RawData):
        run conversion utility
        store converted output

    MOVE original transfer file to archive location

    VERIFY transfer success (e.g., file size match)

    IF verification successful:
        remove temporary/local copy
        remove remote copy (if API-based)

END FOR

END
```

For the transfer mechanism details and site comparison table, see **[Transfer Mechanisms](transfer-mechanisms.md)**. For per-site implementation details, see **[Site Implementations](site-implementations.md)**.