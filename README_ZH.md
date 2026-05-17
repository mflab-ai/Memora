# Memora (Re-Moment)

语言选择:
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: iPadOS 18+](https://img.shields.io/badge/Platform-iPadOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ipados/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora，内部代号 **Re-Moment**，是一款以本地优先为核心的 iPhone/iPad 应用。它会分析用户的照片图库，并把相关的时刻整理成短篇回忆故事视频。应用重点提供私密照片索引、可审核的推荐、可编辑的故事草稿和设备端渲染。Pro Vision AI 是可选的付费功能，用于更高质量的字幕和远程辅助索引。

---

## 主要功能

### 智能故事推荐
* **照片图库索引:** Memora 通过 PhotoKit 读取用户允许访问的照片，并提取日期、地点、收藏、媒体类型、质量、人脸数量、场景和字幕信号。
* **推荐卡片:** 应用会根据同一人物、相似背景、美食、季节、城市/旅行、时间快照、有意义的瞬间和视频高光等生成故事候选。
* **搜索与维护:** 用户可以在本地搜索已索引照片，并使用翻译补全、一致性修复、推荐反馈重置和索引恢复辅助功能。

### 可审核的回忆故事
* **故事审核:** 渲染前可检查推荐故事，替换、删除、添加、重新排序照片，并从人脸清晰的照片中登记代表人物。
* **反馈控制:** 用户可以归档生成的故事、隐藏某条推荐、排除相似推荐类型，并撤销最近的反馈。
* **人物支持:** 已登记的人物资料可用于创建人物主题故事，并改善后续推荐质量。

### 本地优先的 Vision 与存储
* **默认设备端处理:** 标准索引和备用字幕使用本地 PhotoKit、Vision 和元数据分析。除非用户启用并使用 Pro Vision AI，否则照片不会发送到服务器。
* **本地数据库:** 索引、故事、渲染任务、偏好、检查点和人物资料通过 SwiftData 保存在应用沙盒中。可用时，用户也可以选择基于 iCloud Drive 的数据库存储。
* **诊断:** MetricKit 诊断用于排查崩溃、卡顿、启动、CPU 和磁盘写入问题。这些诊断不包含用户的原始照片文件。

### Pro Vision AI
* **可选付费功能:** Pro Vision AI 通过服务器端代理提供增强的 VLM 字幕和远程索引额度管理。额度不可用或无法连接服务器时，应用仍可使用标准本地 Vision AI。
* **服务器端控制:** 后端会验证 StoreKit 权益状态，签发短期访问令牌，执行额度管理，保护提供商 API 密钥，处理幂等性并跟踪滥用防护信号。
* **图像处理:** 图像载荷仅为请求的字幕处理操作而转发。服务设计上不会为产品使用或 AI 训练保存原始图像字节。但为权益、额度、调试、安全和滥用防护目的，可能保留经过清理的请求元数据、提供商响应文本、请求状态、额度计数器、设备哈希和错误信息等运营记录。

### 视频渲染与保存
* **原生渲染器:** 回忆故事基于缓存的照片资源通过 AVFoundation 渲染，默认目标为 30fps，并使用 dissolve、slide、wipe、zoom 类运动与转场效果。
* **导出到 Photos:** 渲染前会在需要时准备 iCloud-only 资源的本地副本。完成的视频通过 Photos add-only 权限和 Photos 兼容 MOV fallback 路径保存。
* **进度与取消:** 应用会显示下载、渲染、保存、失败、取消和恢复状态。

---

## 重要说明

* Memora 需要照片读取权限来索引并推荐故事。支持有限照片访问，但完整访问可提供预期体验。
* 将渲染后的视频保存到照片应用需要照片添加权限。
* Pro Vision AI 会将选定的图像数据发送到后端和配置的 VLM 提供商。请仅用于你愿意进行远程处理的照片。
* AI 生成的字幕和推荐可能不准确。在渲染或分享前请检查故事内容。
* iCloud Drive 数据库存储取决于用户的 Apple iCloud 配置和设备可用性。
* 产品名称、额度、价格和平台支持范围可能在 App Store 发布前后变化。

---

## 技术栈

### 客户端
* Swift 6, SwiftUI, SwiftData
* PhotoKit, Vision, AVFoundation, MetricKit
* MLX Swift LM / MLX VLM 相关包, Swift HuggingFace, Swift Transformers

### 服务器
* FastAPI, Uvicorn, Starlette
* PostgreSQL, SQLAlchemy, Alembic, Psycopg 3
* Pydantic, Pydantic Settings, HTTPX
* 用于 StoreKit 和令牌验证路径的 PyJWT, cryptography

---

## 政策与许可

* [Privacy Policy](./PRIVACY_POLICY.md)
* [Terms of Service](./TERMS_OF_SERVICE.md)
* [Legal Notice](./LEGAL_NOTICE.md)
* [Open Source Licenses](./OPEN_SOURCE_LICENSES.md)
* [Proprietary License](./LICENSE.md)

---

## 许可

Copyright (c) 2026 MFLab-AI. All rights reserved.

除非另有书面许可，Memora 的源代码、资产、品牌、文档和相关材料均为专有内容。第三方开源组件仍受其各自许可证约束。
