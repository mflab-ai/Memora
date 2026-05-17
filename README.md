# Memora (Re-Moment)

🌐 **Select Language / 언어 선택:**
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: macOS 15+](https://img.shields.io/badge/Platform-macOS%2015%2B-lightgrey.svg?style=flat-square&logo=apple)](https://developer.apple.com/macos/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora (internally code-named **Re-Moment**) is a privacy-first, on-device AI-powered smart story collection and photo-slideshow companion. It enables users to automatically group, beautifully caption, and dynamically render cinematic slideshows of their personal memories—all while ensuring that sensitive photo assets and metadata remain strictly under their own control.

---

## 📸 Core Features

### 🧠 Spatio-Temporal Smart Collections
* **Clustering & Recommend Engine:** Automatically groups assets by sophisticated spatial (geographic location) and temporal (time intervals) thresholds into cohesive, contextual events (e.g., *"Weekend in Paris"*, *"Summer Picnic"*).
* **Thematic Diversification:** Combines user preferences, original photo metadata, and visual features into intelligent, structured collection signals and summary cards.

### 🛡️ On-Device Local-First Vision AI
* **Zero-Knowledge Indexing:** Performs primary face grouping, feature indexing, and object recognition entirely on-device utilizing Apple's **CoreML**, **Vision**, and local LLM/VLM runners (**MLX Swift / MLX Swift LM / MLX VLM**).
* **Private Metadata Storage:** Generates summaries, captions, and smart logs safely saved in the device's secure sandbox or synchronized securely via personal **Apple iCloud** accounts.

### ⚡ Pro Vision AI (Cloud-Assisted VLM)
* **High-Fidelity Captions:** Opt-in premium feature providing rich, context-aware captions and deeply detailed tags via advanced Vision-Language Models (VLM).
* **In-Memory Zero-Retention Policy:** Transmitted images are processed purely in-memory on our dedicated FastAPI proxy and are **instantly deleted** immediately after returning the caption. No image logging, storage, or external training ever occurs.

### 🎬 Cinematic Photo Slideshow Rendering
* **Dynamic Transition Engine:** Automatically stitches photo story assets into professional-grade videos using specialized transitions (including *Cross Dissolve, Push, Wipe, Zoom, and Ken Burns effects*).
* **PhotoKit Integration:** Built natively on Apple's **PhotoKit** and **AVFoundation** to support fluid, high-resolution rendering up to 60fps directly on iOS and macOS hardware.

---

## 🔒 Privacy & Data Security Commitment

Memora is engineered under the strict principle of user data sovereignty. We guarantee absolute confidentiality and security regarding your personal photos:

> [!IMPORTANT]
> * **Zero Server-Side Storage:** Any photo transmitted to our servers for the optional "Pro Vision AI" feature is handled exclusively in temporary transient RAM. Your photos are **never** written to disk, saved in databases, cached, or stored on any server logs under any circumstances.
> * **No AI Model Training:** We hold a strict zero-use policy for machine learning development. Your photos, generated descriptions, and private metadata are **never** used to train, fine-tune, or improve any machine learning, VLM, or AI models.
> * **Instant RAM Destruction:** The moment the proxy server responds to your device with the generated caption, all associated image bytes in RAM are **instantly and permanently destroyed**.
> * **On-Device Default:** All fundamental features—such as photo grouping, local indexing, face recognition, and video rendering—run 100% on-device. No network transmission is required unless you explicitly choose to enable Pro Vision AI.

---

## 🛠️ Technology Stack

### Client (iOS / macOS)
* **Language/Frameworks:** Swift 6, SwiftUI, SwiftData, CoreML, Vision, AVFoundation, PhotoKit
* **On-Device AI Ecosystem:** `mlx-swift`, `mlx-swift-lm`, `swift-huggingface`, `swift-transformers`
* **Performance Network & Utilities:** `yyjson` (extreme-performance JSON parser), `EventSource` (SSE streaming API handler), `swift-jinja` (template renderer)

### Server (Python Backend Proxy)
* **API Gateway & Core:** FastAPI, Uvicorn, Starlette, Pydantic & Pydantic Settings
* **Database & Migration:** PostgreSQL, SQLAlchemy (ORM), Alembic, Psycopg 3
* **Cryptographic & Verification:** `cryptography` (Apple App Store API signature checking), `PyJWT` (JWS Token processing)

---

## ⚖️ Policies, Terms & Licensing

Please refer to the following documents for comprehensive information regarding usage policies, terms, and licenses:

* 📄 **[Privacy Policy](./PRIVACY_POLICY.md)** – Comprehensive policy outlining our zero-data retention server policy, on-device local storage, and secure iCloud synchronization.
* 📄 **[Terms of Service](./TERMS_OF_SERVICE.md)** – Terms governing mobile application usage, in-app purchases (IAP) via Apple App Store, and Pro Vision AI quota policies.
* 📄 **[Legal Notice](./LEGAL_NOTICE.md)** – Developer information (MFLab-AI / Sang Hun Kim), intellectual property declarations, and service disclaimers.
* 📄 **[Open Source Licenses](./OPEN_SOURCE_LICENSES.md)** – Detailed list of external third-party libraries and frameworks incorporated in both client and server applications.

---

## 🛡️ License

Copyright (c) 2026 MFLab-AI. All rights reserved.

This project is protected under a proprietary license. For details, please refer to the full license text in the [LICENSE.md](./LICENSE.md) file.

