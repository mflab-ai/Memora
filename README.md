# Memora (Re-Moment)

Select language:
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: iPadOS 18+](https://img.shields.io/badge/Platform-iPadOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ipados/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora, internally code-named **Re-Moment**, is a local-first iPhone and iPad app that analyzes a user's Photos library and turns related moments into short memory-story videos. The app focuses on private photo indexing, reviewable recommendations, editable story drafts, and on-device rendering. Pro Vision AI is an optional paid acceleration path for higher-quality captions and faster remote-assisted indexing.

---

## Core Features

### Smart Story Recommendations
* **Photo library indexing:** Memora reads the user's selected Photos library with PhotoKit and extracts date, location, favorite, media type, quality, face-count, scene, and caption signals.
* **Recommendation cards:** The app builds story candidates such as same-person moments, similar backdrops, food collections, seasonal memories, city/trip views, time snapshots, meaningful moments, and video highlights.
* **Search and maintenance:** Indexed photos can be searched locally, and the app includes maintenance actions for translation backfill, consistency repair, recommendation feedback reset, and indexing recovery.

### Reviewable Memory Stories
* **Story review:** Users can inspect a suggested story before rendering, replace or remove selected photos, add more candidates, reorder assets, and register representative people from face-rich photos.
* **Feedback controls:** Users can archive generated stories, hide a specific recommendation, hide similar recommendation types, and undo recent feedback.
* **People support:** Registered person profiles can be used to build person-focused stories and improve future recommendations.

### Local-First Vision and Storage
* **On-device default:** Standard indexing and fallback captions use local PhotoKit, Vision, and metadata-based analysis. Photos are not sent to the server unless the user enables and uses Pro Vision AI.
* **Local database:** Memora stores indexes, stories, render jobs, preferences, checkpoints, and person profiles in the app sandbox with SwiftData. Users may choose iCloud Drive-backed database storage where available.
* **Diagnostics:** MetricKit diagnostics are used for crash, hang, launch, CPU, and disk-write troubleshooting. These diagnostics do not include the user's photo files.

### Pro Vision AI
* **Optional paid feature:** Pro Vision AI uses a server-side proxy for enhanced VLM captioning and remote indexing quota enforcement. When quota is unavailable or the server cannot be reached, the app remains usable with standard local Vision AI.
* **Server-side control:** The backend verifies StoreKit entitlement state, issues short-lived access tokens, enforces quota, protects provider API keys, applies idempotency, and tracks abuse signals.
* **Image handling:** Image payloads are forwarded only for the requested captioning operation. The service is designed not to store original image bytes for product use or AI training. Operational records such as sanitized request metadata, provider response text, request status, quota counters, device hashes, and error information may be retained for entitlement, quota, debugging, security, and abuse-prevention purposes.

### Video Rendering and Saving
* **Native renderer:** Memory stories are rendered with AVFoundation from cached photo assets at a 30fps target by default, with motion and transition effects such as dissolve, slide, wipe, and zoom-style movement.
* **Photos export:** Before rendering, Memora prepares local copies of iCloud-only assets when needed. Rendered videos are saved back to Photos using add-only permission and Photos-compatible MOV fallback handling.
* **Progress and cancellation:** Download, render, save, failure, cancellation, and recovery states are shown in the app.

---

## Important Notes

* Memora requires Photos read access to index and recommend stories. Limited Photos access is supported, but full access provides the intended experience.
* Saving rendered videos requires Photos add-only permission.
* Pro Vision AI sends selected image data to the backend and configured VLM provider. Use it only for photos you are comfortable processing through the remote service.
* AI-generated captions and recommendations can be inaccurate. Review story contents before rendering or sharing.
* iCloud Drive database storage depends on the user's Apple iCloud configuration and device availability.
* Product names, quotas, prices, and platform availability may change before or after App Store release.

---

## Technology Stack

### Client
* Swift 6, SwiftUI, SwiftData
* PhotoKit, Vision, AVFoundation, MetricKit
* MLX Swift LM / MLX VLM-related packages, Swift HuggingFace, Swift Transformers

### Server
* FastAPI, Uvicorn, Starlette
* PostgreSQL, SQLAlchemy, Alembic, Psycopg 3
* Pydantic, Pydantic Settings, HTTPX
* PyJWT and cryptography for StoreKit and token verification paths

---

## Policies and Licensing

* [Privacy Policy](./PRIVACY_POLICY.md)
* [Terms of Service](./TERMS_OF_SERVICE.md)
* [Legal Notice](./LEGAL_NOTICE.md)
* [Open Source Licenses](./OPEN_SOURCE_LICENSES.md)
* [Proprietary License](./LICENSE.md)

---

## License

Copyright (c) 2026 MFLab-AI. All rights reserved.

Memora's source code, assets, branding, documentation, and related materials are proprietary unless a separate written license says otherwise. Third-party open-source components remain governed by their own licenses.
