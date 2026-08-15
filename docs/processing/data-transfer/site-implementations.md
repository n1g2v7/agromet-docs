# Site Implementations

## ON1 – Google Drive API Transfer

### Overview

* Transfer method: Google Drive API
* Data: tower, TGA, manual, logbook
* Automation: Python + Task Scheduler

### Workflow Summary

* Site: collect → rename → zip → upload
* Lab: download → unzip → organize → archive → cleanup

### Destinations

**Main repository**

```
ses-lab-data\E26\hfdata\...
ses-lab-data\E26\database\...
```

**Mirror copy**

```
ses-lab-data\Guelph_agromet\sites\ON1\...
```

**Transfer archive**

```
ses-lab-data\Transfers\E26\...
```

### Notes

* Files copied to both main repository and mirror
* ZIP files archived after processing
* Files removed from Drive only after verification

## ON3 – Google Drive API Transfer

!!! info "Stub — content to be added"
    This section follows the same architecture as ON1 but with site-specific
    paths and configuration. Details to be completed once ON1 documentation
    is finalised and used as a template.

### Overview

* Same architecture as ON1
* Different site configuration and paths

### Differences from ON1

* station naming
* directory structure
* fewer/more instruments

## SK1 – Dropbox + Google API (Hybrid)

!!! info "Stub — content to be added"
    Site-specific paths, Dropbox folder configuration, and script names to be
    documented here.

### Overview

* Tower + TGA: Dropbox
* Manual data: Google API

### Workflow Summary

* Dropbox handles high-frequency data
* API handles manual/logbook files

### Key Differences

* No upload script for tower data
* Sync timing depends on Dropbox
* No automatic deletion of remote files

## AB1 – Hybrid Transfer

!!! info "Stub — content to be added"
    Site-specific paths and script names to be documented here.

### Overview

* Uses Google API for TGA + manual data
* Additional scripts for SmartFlux / summary data

### Notes

* Multiple independent ingestion paths
* Requires coordination at processing stage

## AB2 – DriveHQ + Google API (Hybrid)

!!! info "Stub — content to be added"
    Site-specific DriveHQ retrieval details and script names to be documented here.

### Overview

* Tower data: DriveHQ
* TGA + manual: Google API

### Workflow Summary

* DriveHQ used for tower (SmartFlux) datasets
* API used for TGA and other structured datasets

### Key Differences

* External cloud replaces site upload script
* Lab retrieval handled separately
* Integrated downstream with same processing pipeline

## Summary

Despite different transfer mechanisms, all sites converge into a unified workflow:

```
Transfer → Staging → Organization → Archive → Processing
```

This design allows flexibility at the site level while maintaining consistency in downstream processing.