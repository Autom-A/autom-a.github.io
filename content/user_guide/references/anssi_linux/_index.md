---
title: "ANSSI - Linux"
date: 2023-12-08T22:33:38+01:00
draft: false
---

> last update : December 8, 2023

## Debian 12

### Applicability

```mermaid
%%{
    init: {
        "theme": "base",
        "themeVariables": {
            "pie1": "#b6d7a8",
            "pie2": "#e06666",
            "pie3": "#ffe599"
        }
    }
}%%
pie title Applicability rate in AutomA
    "YES" : 49
    "NO" : 11
    "?" : 20 
```

Below is a list of non-applicable rules:

|Number|Level|Name|
|:---:|:---:|---|
|R1|Reinforced|Choosing and configuring your equipment|
|R2|Intermediate|Configure BIOS/UEFI|
|R3|Intermediate|Enable UEFI secure boot|
|R4|High|Replace preloaded keys|
|R28|Intermediate|Standard partitioning|
|R64|Reinforced|Configuring service privileges|
|R65|Reinforced|Partitioning services|
|R66|High|Hardening of partitioning components|
|R76|High|Sealing and verifying file integrity|
|R77|High|Protecting the seal database|
|R78|Reinforced|Enclosing network services|


### Testing platform

```mermaid
%%{
    init: {
        "theme": "base",
        "themeVariables": {
            "pie1": "#674ea7",
            "pie2": "#ff00ff",
            "pie3": "#d9d9d9"
        }
    }
}%%
pie title Testing platform distribution
    "Docker" : 6
    "VM" : 2
    "?" : 61
```

### Coverage

```mermaid
%%{
    init: {
        "theme": "base",
        "themeVariables": {
            "pie1": "#4285f4",
            "pie2": "#ffff00",
            "pie3": "#00ff00"
        }
    }
}%%
pie title Repository coverage rate
    "TODO" : 60
    "IN PROGRESS" : 1
    "DONE" : 8
```

## Files

You will find all the files containing the data presented.

{{% notice title="Progress files" color="#2e738d" icon="fas fa-link" %}}
- [anssi.debian.12.json](/files/anssi.debian.12.json)
{{% /notice %}}