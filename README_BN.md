# Memora (Re-Moment)

ভাষা নির্বাচন:
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: iPadOS 18+](https://img.shields.io/badge/Platform-iPadOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ipados/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora, অভ্যন্তরীণ কোডনাম **Re-Moment**, iPhone এবং iPad-এর জন্য একটি local-first অ্যাপ। এটি ব্যবহারকারীর Photos library বিশ্লেষণ করে সম্পর্কিত মুহূর্তগুলোকে ছোট memory-story video-তে রূপান্তর করে। অ্যাপটি private photo indexing, reviewable recommendations, editable story drafts এবং on-device rendering-এ গুরুত্ব দেয়। Pro Vision AI উচ্চমানের captions এবং remote-assisted indexing-এর জন্য একটি optional paid feature।

---

## প্রধান বৈশিষ্ট্য

### Smart Story Recommendations
* **Photo library indexing:** Memora PhotoKit দিয়ে ব্যবহারকারী অনুমোদিত photos পড়ে date, location, favorite, media type, quality, face-count, scene এবং caption signals বের করে।
* **Recommendation cards:** অ্যাপটি same-person moments, similar backdrops, food collections, seasonal memories, city/trip views, time snapshots, meaningful moments এবং video highlights থেকে story candidates তৈরি করে।
* **Search and maintenance:** Indexed photos locally search করা যায়। অ্যাপে translation backfill, consistency repair, recommendation feedback reset এবং indexing recovery সহায়তাও আছে।

### Reviewable Memory Stories
* **Story review:** Rendering-এর আগে ব্যবহারকারী suggested story দেখতে পারে, photos replace/remove/add করতে পারে, assets reorder করতে পারে এবং face-rich photos থেকে representative people register করতে পারে।
* **Feedback controls:** ব্যবহারকারী generated stories archive করতে পারে, নির্দিষ্ট recommendation hide করতে পারে, similar recommendation types hide করতে পারে এবং recent feedback undo করতে পারে।
* **People support:** Registered person profiles person-focused stories তৈরি করতে এবং future recommendations উন্নত করতে ব্যবহৃত হয়।

### Local-First Vision and Storage
* **On-device default:** Standard indexing এবং fallback captions local PhotoKit, Vision এবং metadata-based analysis দিয়ে চলে। ব্যবহারকারী Pro Vision AI enable এবং use না করলে photos server-এ পাঠানো হয় না।
* **Local database:** Memora indexes, stories, render jobs, preferences, checkpoints এবং person profiles SwiftData দিয়ে app sandbox-এ store করে। যেখানে available, ব্যবহারকারী iCloud Drive-backed database storage বেছে নিতে পারে।
* **Diagnostics:** MetricKit diagnostics crash, hang, launch, CPU এবং disk-write issues troubleshoot করতে ব্যবহৃত হয়। এতে ব্যবহারকারীর original photo files থাকে না।

### Pro Vision AI
* **Optional paid feature:** Pro Vision AI enhanced VLM captioning এবং remote indexing quota enforcement-এর জন্য server-side proxy ব্যবহার করে। quota না থাকলে বা server unavailable হলে app standard local Vision AI দিয়ে usable থাকে।
* **Server-side control:** Backend StoreKit entitlement state verify করে, short-lived access tokens issue করে, quota enforce করে, provider API keys protect করে, idempotency apply করে এবং abuse signals track করে।
* **Image handling:** Image payloads শুধু requested captioning operation-এর জন্য forward করা হয়। Service original image bytes product use বা AI training-এর জন্য store না করার জন্য designed। Entitlement, quota, debugging, security এবং abuse-prevention-এর জন্য sanitized request metadata, provider response text, request status, quota counters, device hashes এবং error information-এর মতো operational records রাখা হতে পারে।

### Video Rendering and Saving
* **Native renderer:** Memory stories cached photo assets থেকে AVFoundation দিয়ে default 30fps target-এ render হয়, dissolve, slide, wipe এবং zoom-style motion/transition effects সহ।
* **Photos export:** Rendering-এর আগে Memora প্রয়োজন হলে iCloud-only assets-এর local copies প্রস্তুত করে। Rendered videos Photos add-only permission এবং Photos-compatible MOV fallback handling দিয়ে save হয়।
* **Progress and cancellation:** App download, render, save, failure, cancellation এবং recovery states দেখায়।

---

## গুরুত্বপূর্ণ নোট

* Memora stories index এবং recommend করতে Photos read access প্রয়োজন। Limited Photos access supported, তবে full access intended experience দেয়।
* Rendered videos Photos-এ save করতে Photos add-only permission লাগে।
* Pro Vision AI selected image data backend এবং configured VLM provider-এ পাঠায়। Remote processing করতে স্বাচ্ছন্দ্যবোধ করেন এমন photos-এর জন্যই ব্যবহার করুন।
* AI-generated captions এবং recommendations inaccurate হতে পারে। Render বা share করার আগে story content review করুন।
* iCloud Drive database storage ব্যবহারকারীর Apple iCloud configuration এবং device availability-এর ওপর নির্ভর করে।
* Product names, quotas, prices এবং platform availability App Store release-এর আগে বা পরে পরিবর্তিত হতে পারে।

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
* StoreKit এবং token verification paths-এর জন্য PyJWT এবং cryptography

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

আলাদা লিখিত license না থাকলে Memora-এর source code, assets, branding, documentation এবং related materials proprietary। Third-party open-source components তাদের নিজস্ব licenses অনুসরণ করে।
