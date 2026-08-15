# Collection Logic & Next Steps

## Collection Logic (Conceptual Pseudocode)

```text
FOR each field datalogger:
    measure connected sensors according to logger scan program
    write values to logger memory and output tables

FOR each LoggerNet-supported logger:
    at scheduled collection times:
        poll logger from site computer
        retrieve new table records
        save exported files locally on the site computer

FOR each non-LoggerNet legacy logger:
    during field visit:
        connect field laptop to logger
        manually download records
        manually hand off downloaded files into the downstream data-transfer path
```

## Next Workflow Stage

This section covers the **collection layer only**.

After collection:

- LoggerNet-supported outputs reside on the **site computer**
- shallow-soil legacy outputs reside on a **field laptop until manually moved**
- both then feed into the **Data Transfer Workflow**

See **[Transfer Architecture & Workflow](../data-transfer/architecture-workflow.md)** for the next stage in the operational chain.