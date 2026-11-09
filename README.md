# Magnetar Client Modules

## 📦 What is this Repository?

This repository acts as the public CDN and versioning mirror for assets used by the **Magnetar Client** ecosystem:

## 🔄 How the Sync System Works

```mermaid
sequenceDiagram
    autonumber
    participant Client as Magnetar Client (Mod)
    participant Server as Magnetar Server
    participant GH as GitHub Releases (This Repo)

    Client->>Server: Check model version (If-None-Match)
    alt Model is Up to Date
        Server-->>Client: 304 Not Modified (0 bytes transferred)
        Client->>Client: Keep local model in memory
    else Model Update Available
        Server-->>Client: 302 Found (Redirect to GitHub CDN)
        Client->>GH: Download buff_model.zip
        GH-->>Client: High-speed CDN stream
        Client->>Client: Apply model & update local metadata
    end
```
