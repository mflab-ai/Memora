# Memora (Re-Moment)

🌐 **Select Language / 언어 선택:**
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: macOS 15+](https://img.shields.io/badge/Platform-macOS%2015%2B-lightgrey.svg?style=flat-square&logo=apple)](https://developer.apple.com/macos/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora（内部项目代号为 **Re-Moment**）是一款以用户隐私为核心、基于端侧（On-Device）AI 的智能故事画册与照片幻灯片制作应用。在确保用户对敏感照片资产和元数据拥有绝对控制权的前提下，应用利用 AI 自动进行主题分组、生成优美的叙事字幕，并渲染出电影级质感的故事幻灯片视频。

---

## 📸 核心功能 (Core Features)

### 🧠 时空智能聚合 (Spatio-Temporal Smart Collections)
* **聚类与推荐引擎：** 采用先进的空间（地理位置）和时间（时间间隔）阈值算法，自动将用户的照片资产归类为连贯且有逻辑的事件包（例如 *"巴黎周末"*, *"夏日野餐"*）。
* **主题多样化：** 结合用户偏好、照片原始元数据和视觉特征，生成智能且结构化的聚合信号和摘要卡片。

### 🛡️ 端侧隐私原生视觉 AI (On-Device Vision AI)
* **零知识索引 (Zero-Knowledge Indexing)：** 充分利用苹果的 **CoreML**、**Vision** 以及本地 LLM/VLM 运行框架（**MLX Swift / MLX Swift LM / MLX VLM**），在设备本地 100% 独立运行照片分析、索引和人脸识别，无需向外部服务器发送任何照片数据。
* **本地安全存储：** 生成的故事描述、字幕和分析日志安全地保存在设备内部的安全沙盒中，或者通过用户启用的个人 **Apple iCloud** 账户进行安全加密同步。

### ⚡ 专业视觉 AI (Pro Vision AI - 云端联动 VLM)
* **高精度字幕生成：** 属于高级可选功能，利用先进的视觉语言模型（VLM）为照片生成细节丰富、情境契合的叙事文字及精准标签。
* **内存零留存处理政策 (In-Memory Zero-Retention Policy)：** 传输到服务器的图像仅在临时挥发性内存（RAM）中进行实时处理，一旦字幕生成完毕并返回，**立即从服务器端 100% 永久销毁**。绝不在任何地方存储图像、记录日志或用于模型训练。

### 🎬 电影级幻灯片视频渲染 (Slideshow Rendering)
* **动态转场引擎：** 自动应用精细调校的特殊过渡效果（包括*交叉溶解、推入、擦除、缩放和肯·巴恩斯特效*等），将静态故事照片无缝拼接为高水准的纪录片级视听视频。
* **PhotoKit 原生集成：** 基于苹果的 **PhotoKit** 和 **AVFoundation** 原生开发，支持直接在 iOS 和 macOS 硬件上渲染出最高 60fps 的流畅、超清视频。

---

## 🔒 隐私与数据安全庄严承诺 (Privacy & Data Security Commitment)

Memora 的设计基石是捍卫用户的“数据主权”（Data Sovereignty）。我们向您承诺，对您宝贵的个人照片信息实行绝对的安全保障与机密维护。

> [!IMPORTANT]
> * **云端存储源头杜绝 (Zero Server-Side Storage)：** 为使用可选的“Pro Vision AI”功能而传输至我们服务器的所有照片，仅在临时挥发性内存（RAM）中进行短暂处理。用户的照片在任何情况下都不会写入磁盘、不会存入数据库、不会被缓存，也不会在服务器日志中留下任何痕迹。
> * **严禁用于 AI 模型训练与开发 (No AI Model Training)：** 我们遵循铁律般的“零使用政策”（Zero-Use Policy）。用户的照片、生成的文本描述以及个人元数据，**绝不会**被用于任何大语言模型（LLM）、视觉语言模型（VLM）或任何 AI 模型的训练、微调（Fine-Tuning）与优化。
> * **瞬时 RAM 销毁 (Instant RAM Destruction)：** 代理服务器将生成的字幕文本传回用户设备的刹那，RAM 中驻留的所有图像字节数据将**立即且彻底地被销毁与清除**。
> * **本地端侧默认 (On-Device Default)：** 照片主题分组、本地索引、人脸识别、幻灯片视频渲染等应用的所有基础功能均 100% 在本地设备中运行。除非您主动开启 Pro Vision AI 功能，否则绝不会发生任何网络照片传输。

---

## 🛠️ 技术栈 (Technology Stack)

### 客户端 (iOS / macOS)
* **语言与框架：** Swift 6, SwiftUI, SwiftData, CoreML, Vision, AVFoundation, PhotoKit
* **端侧 AI 生态：** `mlx-swift`, `mlx-swift-lm`, `swift-huggingface`, `swift-transformers`
* **高性能及网络组件：** `yyjson`（超高速 JSON 解析器）, `EventSource`（SSE 流式 API 处理器）, `swift-jinja`（模板渲染器）

### 服务端 (Python Backend Proxy)
* **API 网关与核心：** FastAPI, Uvicorn, Starlette, Pydantic & Pydantic Settings
* **数据库与迁移工具：** PostgreSQL, SQLAlchemy (ORM), Alembic, Psycopg 3
* **加密与安全验证：** `cryptography`（苹果 App Store API 签名验证）, `PyJWT`（JWS 令牌处理）

---

## ⚖️ 相关政策与许可声明 (Policies & Licensing)

关于更具体和详细的法律声明和隐私条款，请参阅并关联以下文档：

* 📄 **[隐私政策 (Privacy Policy)](./PRIVACY_POLICY.md)** – 零数据服务器无留存原则、端侧本地存储和 iCloud 安全同步的总体规范。
* 📄 **[服务条款 (Terms of Service)](./TERMS_OF_SERVICE.md)** – 移动应用使用规范、通过 Apple App Store 进行的内购（IAP）以及 Pro Vision AI 额度管理政策。
* 📄 **[法律声明 (Legal Notice)](./LEGAL_NOTICE.md)** – 开发者信息（MFLab-AI / 金相勋）、知识产权声明及服务免责范围告知。
* 📄 **[开源授权声明 (Open Source Licenses)](./OPEN_SOURCE_LICENSES.md)** – 客户端及服务端软件中集成的所有第三方外部开源库清单及对应授权协议。

---

## 🛡️ 版权与授权协议 (License)

Copyright (c) 2026 MFLab-AI. All rights reserved.

本项目受专有许可证保护。欲了解详情，请参阅 [LICENSE.md](./LICENSE.md) 文件中的完整许可证文本。

