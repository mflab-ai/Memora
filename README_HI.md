# Memora (Re-Moment)

भाषा चुनें:
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: iPadOS 18+](https://img.shields.io/badge/Platform-iPadOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ipados/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora, आंतरिक कोड नाम **Re-Moment**, iPhone और iPad के लिए local-first ऐप है जो उपयोगकर्ता की Photos library का विश्लेषण करके संबंधित पलों को छोटे memory-story videos में बदलता है। ऐप निजी फोटो इंडेक्सिंग, समीक्षा योग्य recommendations, editable story drafts और on-device rendering पर केंद्रित है। Pro Vision AI बेहतर captions और remote-assisted indexing के लिए optional paid feature है।

---

## मुख्य विशेषताएं

### Smart Story Recommendations
* **Photo library indexing:** Memora PhotoKit से उपयोगकर्ता द्वारा अनुमति दी गई photos पढ़ता है और date, location, favorite, media type, quality, face-count, scene और caption signals निकालता है।
* **Recommendation cards:** ऐप same-person moments, similar backdrops, food collections, seasonal memories, city/trip views, time snapshots, meaningful moments और video highlights जैसे story candidates बनाता है।
* **Search and maintenance:** Indexed photos को locally search किया जा सकता है। ऐप translation backfill, consistency repair, recommendation feedback reset और indexing recovery सहायता भी देता है।

### Reviewable Memory Stories
* **Story review:** Rendering से पहले उपयोगकर्ता suggested story देख सकता है, photos replace/remove/add कर सकता है, assets reorder कर सकता है और face-rich photos से representative people register कर सकता है।
* **Feedback controls:** उपयोगकर्ता generated stories archive कर सकता है, किसी specific recommendation को hide कर सकता है, similar recommendation types छिपा सकता है और recent feedback undo कर सकता है।
* **People support:** Registered person profiles person-focused stories बनाने और future recommendations सुधारने में उपयोग होते हैं।

### Local-First Vision and Storage
* **On-device default:** Standard indexing और fallback captions local PhotoKit, Vision और metadata-based analysis से चलते हैं। जब तक उपयोगकर्ता Pro Vision AI enable और use नहीं करता, photos server पर नहीं भेजी जातीं।
* **Local database:** Memora indexes, stories, render jobs, preferences, checkpoints और person profiles को SwiftData के साथ app sandbox में store करता है। जहां उपलब्ध हो, उपयोगकर्ता iCloud Drive-backed database storage चुन सकता है।
* **Diagnostics:** MetricKit diagnostics crash, hang, launch, CPU और disk-write issues की troubleshooting के लिए उपयोग होते हैं। इनमें उपयोगकर्ता की original photo files शामिल नहीं होतीं।

### Pro Vision AI
* **Optional paid feature:** Pro Vision AI enhanced VLM captioning और remote indexing quota enforcement के लिए server-side proxy का उपयोग करता है। quota न होने या server unavailable होने पर ऐप standard local Vision AI के साथ usable रहता है।
* **Server-side control:** Backend StoreKit entitlement state verify करता है, short-lived access tokens issue करता है, quota enforce करता है, provider API keys protect करता है, idempotency apply करता है और abuse signals track करता है।
* **Image handling:** Image payloads केवल requested captioning operation के लिए forward किए जाते हैं। Service original image bytes को product use या AI training के लिए store न करने के लिए designed है। Entitlement, quota, debugging, security और abuse-prevention के लिए sanitized request metadata, provider response text, request status, quota counters, device hashes और error information जैसे operational records रखे जा सकते हैं।

### Video Rendering and Saving
* **Native renderer:** Memory stories cached photo assets से AVFoundation द्वारा default 30fps target पर render होती हैं, जिनमें dissolve, slide, wipe और zoom-style motion/transition effects होते हैं।
* **Photos export:** Rendering से पहले Memora जरूरत पड़ने पर iCloud-only assets की local copies तैयार करता है। Rendered videos Photos add-only permission और Photos-compatible MOV fallback handling से save होते हैं।
* **Progress and cancellation:** App download, render, save, failure, cancellation और recovery states दिखाता है।

---

## महत्वपूर्ण नोट्स

* Memora को stories index और recommend करने के लिए Photos read access चाहिए। Limited Photos access supported है, लेकिन full access intended experience देता है।
* Rendered videos को Photos में save करने के लिए Photos add-only permission चाहिए।
* Pro Vision AI selected image data को backend और configured VLM provider को भेजता है। इसे केवल उन photos के लिए use करें जिन्हें आप remote processing के लिए comfortable मानते हैं।
* AI-generated captions और recommendations inaccurate हो सकते हैं। Render या share करने से पहले story content review करें।
* iCloud Drive database storage उपयोगकर्ता की Apple iCloud configuration और device availability पर निर्भर करता है।
* Product names, quotas, prices और platform availability App Store release से पहले या बाद में बदल सकते हैं।

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
* StoreKit और token verification paths के लिए PyJWT और cryptography

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

जब तक अलग लिखित license न हो, Memora का source code, assets, branding, documentation और related materials proprietary हैं। Third-party open-source components अपने licenses के अधीन रहते हैं।
