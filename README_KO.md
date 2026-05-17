# Memora (Re-Moment)

🌐 **Select Language / 언어 선택:**
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: macOS 15+](https://img.shields.io/badge/Platform-macOS%2015%2B-lightgrey.svg?style=flat-square&logo=apple)](https://developer.apple.com/macos/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora (내부 프로젝트명 **Re-Moment**)는 프라이버시를 최우선으로 하는 온디바이스 AI 기반 스마트 스토리 컬렉션 및 사진 슬라이드쇼 제작 앱입니다. 사용자는 개인의 민감한 사진 자산과 메타데이터에 대해 완벽한 통제권을 유지하면서, AI가 자동으로 테마별로 묶고 아름다운 내러티브 캡션을 작성하며 영화 같은 슬라이드쇼 비디오를 렌더링하는 혁신을 경험할 수 있습니다.

---

## 📸 핵심 기능 (Core Features)

### 🧠 시공간 기반 스마트 컬렉션 (Spatio-Temporal Smart Collections)
* **클러스터링 및 추천 엔진:** 고도화된 공간적(지리적 위치) 및 시간적(시간 간격) 임계값 알고리즘을 적용하여 사용자의 사진 자산을 하나의 응집력 있고 맥락 있는 이벤트(예: *"파리에서의 주말"*, *"여름 피크닉"*)로 자동 그룹화합니다.
* **테마의 다각화:** 사용자의 선호도, 사진 고유의 메타데이터, 그리고 시각적 특징을 결합하여 지능적이고 구조화된 컬렉션 신호와 요약 카드를 생성합니다.

### 🛡️ 프라이버시 퍼스트 온디바이스 비전 AI (On-Device Vision AI)
* **제로-놀리지 인덱싱 (Zero-Knowledge Indexing):** 애플의 **CoreML**, **Vision** 및 로컬 LLM/VLM 러너(**MLX Swift / MLX Swift LM / MLX VLM**)를 활용하여 사진 분석, 인덱싱, 얼굴 인식 등 핵심 처리를 외부 서버 전송 없이 100% 기기 내에서만 독립적으로 실행합니다.
* **로컬 보안 메타데이터 보관:** 생성된 설명문, 캡션 및 스마트 분석 로그는 기기 내부의 안전한 샌드박스에 로컬 저장되거나, 사용자가 활성화한 개인 **Apple iCloud** 계정을 통해 안전하게 동기화됩니다.

### ⚡ 프로 비전 AI (Pro Vision AI - 클라우드 연동 VLM)
* **고정밀 캡션 생성:** 고급 시각 언어 모델(VLM)을 활용하여 풍부하고 맥락 파악이 뛰어난 문장 캡션과 정밀한 태그를 생성하는 프리미엄 옵션 기능입니다.
* **인메모리 무기록 처리 정책 (In-Memory Zero-Retention Policy):** 전송된 이미지는 오직 휘발성 메모리(RAM) 상에서만 임시 처리되며, 캡션이 생성되는 즉시 **서버에서 100% 영구 삭제**됩니다. 이미지 저장, 로그 기록, 혹은 모델 학습에 절대 활용되지 않습니다.

### 🎬 영화 같은 사진 슬라이드쇼 비디오 렌더링 (Slideshow Rendering)
* **동적 트랜지션 엔진:** 정밀하게 조정된 특수 전환 효과(*Cross Dissolve, Push, Wipe, Zoom, Ken Burns 효과* 등)를 적용하여 사진 스토리를 전문 다큐멘터리 수준의 시네마틱 동영상으로 엮어냅니다.
* **PhotoKit 네이티브 연동:** 애플의 **PhotoKit** 및 **AVFoundation**에 기반하여 개발되어 iOS 및 macOS 하드웨어에서 직접 최대 60fps의 부드럽고 선명한 고해상도 비디오를 렌더링합니다.

---

## 🔒 프라이버시 및 데이터 보안 서약 (Privacy & Data Security Commitment)

Memora는 사용자의 데이터 주권(Data Sovereignty) 수호라는 엄격한 원칙 하에 설계되었습니다. 당사는 사용자의 소중한 사진 정보에 대해 절대적인 비밀 유지와 보안을 보장합니다.

> [!IMPORTANT]
> * **서버 저장 원천 배제 (Zero Server-Side Storage):** 옵션 기능인 "Pro Vision AI"를 위해 당사 서버로 전송된 모든 사진은 오직 임시 휘발성 메모리(RAM) 내에서만 일시적으로 처리됩니다. 사용자의 사진은 어떠한 경우에도 디스크에 기록되지 않으며, 데이터베이스에 보관되거나 캐싱되거나 서버 로그에 남겨지지 않습니다.
> * **AI 모델 학습 및 개발 사용 전면 금지 (No AI Model Training):** 당사는 인공지능 개발에 대한 철저한 무사용 정책(Zero-Use Policy)을 따릅니다. 사용자의 사진, 생성된 설명문 및 개인 메타데이터는 대형 언어 모델(LLM), 시각 언어 모델(VLM) 또는 어떠한 AI 모델의 학습 및 미세조정(Fine-Tuning) 용도로도 **절대 사용되지 않습니다.**
> * **즉각적인 RAM 파괴 (Instant RAM Destruction):** 프록시 서버가 사용자의 기기로 생성된 캡션 텍스트를 반환하여 전달하는 바로 그 순간, RAM에 상주하던 모든 이미지 바이트 데이터는 **즉시 그리고 완전히 파괴 및 삭제**됩니다.
> * **온디바이스 기본 작동 (On-Device Default):** 사진의 그룹화, 로컬 인덱싱, 얼굴 인식, 슬라이드쇼 비디오 렌더링 등 앱의 모든 근간 기능은 100% 로컬 기기 내에서 동작합니다. 사용자가 프로 비전 AI를 명시적으로 활성화하지 않는 한, 네트워크를 통한 이미지 전송은 전혀 발생하지 않습니다.

---

## 🛠️ 기술 스택 (Technology Stack)

### 클라이언트 (iOS / macOS)
* **언어 및 프레임워크:** Swift 6, SwiftUI, SwiftData, CoreML, Vision, AVFoundation, PhotoKit
* **온디바이스 AI 생태계:** `mlx-swift`, `mlx-swift-lm`, `swift-huggingface`, `swift-transformers`
* **고성능 및 네트워크 유틸리티:** `yyjson` (초고속 JSON 파서), `EventSource` (SSE 스트리밍 API 핸들러), `swift-jinja` (템플릿 렌더러)

### 서버 (Python Backend Proxy)
* **API 게이트웨이 및 코어:** FastAPI, Uvicorn, Starlette, Pydantic & Pydantic Settings
* **데이터베이스 및 마이그레이션:** PostgreSQL, SQLAlchemy (ORM), Alembic, Psycopg 3
* **암호화 및 검증:** `cryptography` (애플 앱스토어 API 서명 확인), `PyJWT` (JWS 토큰 처리)

---

## ⚖️ 제반 정책 및 라이선스 (Policies & Licensing)

보다 구체적이고 자세한 법적 고지 및 방침에 대해서는 다음 문서들을 연계하여 참조하십시오.

* 📄 **[개인정보 처리방침 (Privacy Policy)](./PRIVACY_POLICY.md)** – 제로 데이터 서버 무저장 원칙, 온디바이스 로컬 보관, 보안 iCloud 동기화에 대한 총체적 명세.
* 📄 **[서비스 이용약관 (Terms of Service)](./TERMS_OF_SERVICE.md)** – 모바일 애플리케이션 사용 규정, 애플 앱스토어를 통한 인앱 결제(IAP), 및 프로 비전 AI 사용 할당량 정책.
* 📄 **[법적 고지 (Legal Notice)](./LEGAL_NOTICE.md)** – 개발자 정보(MFLab-AI / 김상훈), 지적재산권 선언 및 서비스 책임 한계 고지.
* 📄 **[오픈소스 라이선스 (Open Source Licenses)](./OPEN_SOURCE_LICENSES.md)** – 클라이언트 및 서버 프로그램에 탑재된 모든 타사 외부 오픈소스 라이브러리 목록 및 라이선스 고지.

---

## 🛡️ 저작권 및 라이선스 (License)

Copyright (c) 2026 MFLab-AI. All rights reserved.

본 프로젝트는 독점 라이선스 하에 보호됩니다. 자세한 내용은 [LICENSE.md](./LICENSE.md) 파일에서 전체 라이선스 텍스트를 참조하십시오.

