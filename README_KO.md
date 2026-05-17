# Memora (Re-Moment)

언어 선택:
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: iPadOS 18+](https://img.shields.io/badge/Platform-iPadOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ipados/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora, 내부 프로젝트명 **Re-Moment**,는 사용자의 사진 보관함을 로컬 우선 방식으로 분석해 관련 있는 순간들을 짧은 추억 스토리 영상으로 만드는 iPhone/iPad 앱입니다. 핵심은 비공개 사진 인덱싱, 검토 가능한 추천, 편집 가능한 스토리 초안, 기기 내 렌더링입니다. Pro Vision AI는 더 풍부한 캡션과 원격 보조 인덱싱을 위한 선택형 유료 기능입니다.

---

## 주요 기능

### 스마트 스토리 추천
* **사진 보관함 인덱싱:** PhotoKit으로 사용자가 허용한 사진을 읽고 날짜, 위치, 즐겨찾기, 미디어 타입, 품질, 얼굴 수, 장면, 캡션 신호를 추출합니다.
* **추천 카드:** 같은 인물, 비슷한 배경, 음식, 계절, 도시/여행, 시간 스냅샷, 의미 있는 순간, 비디오 하이라이트 등 다양한 기준으로 스토리 후보를 만듭니다.
* **검색 및 유지관리:** 인덱싱된 사진을 로컬에서 검색할 수 있고, 번역 보강, 정합성 복구, 추천 피드백 초기화, 인덱싱 재개 보조 기능을 제공합니다.

### 검토 가능한 메모리 스토리
* **스토리 리뷰:** 렌더링 전에 추천 스토리를 확인하고, 사진 교체/제거/추가/정렬을 조정하며, 얼굴이 잘 나온 사진에서 대표 인물을 등록할 수 있습니다.
* **피드백 제어:** 생성된 스토리를 아카이브하거나 특정 추천을 숨기고, 비슷한 추천 유형을 제외하거나 최근 피드백을 되돌릴 수 있습니다.
* **인물 지원:** 등록된 인물 프로필은 인물 중심 스토리 구성과 이후 추천 품질 개선에 사용됩니다.

### 로컬 우선 Vision 및 저장
* **기본은 온디바이스:** 일반 인덱싱과 대체 캡션은 로컬 PhotoKit, Vision, 메타데이터 기반 분석으로 처리됩니다. 사용자가 Pro Vision AI를 켜고 사용할 때가 아니면 사진이 서버로 전송되지 않습니다.
* **로컬 데이터베이스:** 인덱스, 스토리, 렌더 작업, 설정, 체크포인트, 인물 프로필은 SwiftData로 앱 샌드박스에 저장됩니다. 가능한 기기에서는 iCloud Drive 기반 데이터베이스 저장을 선택할 수 있습니다.
* **진단 정보:** MetricKit 진단은 충돌, 멈춤, 실행, CPU, 디스크 쓰기 문제를 파악하기 위해 사용됩니다. 이 진단에는 사용자의 사진 파일이 포함되지 않습니다.

### Pro Vision AI
* **선택형 유료 기능:** Pro Vision AI는 서버 프록시를 통해 향상된 VLM 캡션과 원격 인덱싱 처리량을 제공합니다. 처리량이 없거나 서버에 연결할 수 없어도 앱은 일반 Vision AI로 계속 사용할 수 있습니다.
* **서버 측 통제:** 백엔드는 StoreKit 권한 상태를 검증하고, 단기 액세스 토큰을 발급하며, 처리량을 관리하고, 제공자 API 키를 보호하고, 멱등성과 어뷰징 방지 신호를 처리합니다.
* **이미지 처리:** 이미지 페이로드는 요청된 캡션 처리 목적에 한해 전달됩니다. 서비스는 원본 이미지 바이트를 제품 기능이나 AI 학습 목적으로 저장하지 않도록 설계되어 있습니다. 다만 권한, 처리량, 디버깅, 보안, 어뷰징 방지를 위해 정제된 요청 메타데이터, 제공자 응답 텍스트, 요청 상태, 처리량 카운터, 디바이스 해시, 오류 정보 같은 운영 기록은 보관될 수 있습니다.

### 비디오 렌더링 및 저장
* **네이티브 렌더러:** 메모리 스토리는 캐시된 사진 자산을 바탕으로 AVFoundation에서 기본 30fps 목표로 렌더링되며, dissolve, slide, wipe, zoom 계열 움직임과 전환 효과를 사용합니다.
* **사진 앱 저장:** 렌더링 전 iCloud 전용 자산의 로컬 사본을 준비하고, 완성된 영상은 Photos add-only 권한과 Photos 호환 MOV fallback 경로를 통해 저장합니다.
* **진행 상태:** 다운로드, 렌더링, 저장, 실패, 취소, 복구 상태를 앱에서 표시합니다.

---

## 주의사항

* Memora는 스토리 추천을 위해 사진 읽기 권한이 필요합니다. 제한된 사진 접근도 지원하지만, 전체 접근에서 의도한 경험을 제공합니다.
* 렌더링된 영상을 사진 앱에 저장하려면 사진 추가 권한이 필요합니다.
* Pro Vision AI는 선택된 이미지 데이터를 백엔드와 설정된 VLM 제공자에 전송합니다. 원격 처리해도 괜찮은 사진에만 사용하세요.
* AI가 만든 캡션과 추천은 부정확할 수 있습니다. 렌더링하거나 공유하기 전에 스토리 내용을 확인하세요.
* iCloud Drive 데이터베이스 저장은 사용자의 Apple iCloud 설정과 기기 상태에 따라 달라집니다.
* 상품명, 처리량, 가격, 플랫폼 지원 범위는 App Store 출시 전후로 변경될 수 있습니다.

---

## 기술 스택

### 클라이언트
* Swift 6, SwiftUI, SwiftData
* PhotoKit, Vision, AVFoundation, MetricKit
* MLX Swift LM / MLX VLM 관련 패키지, Swift HuggingFace, Swift Transformers

### 서버
* FastAPI, Uvicorn, Starlette
* PostgreSQL, SQLAlchemy, Alembic, Psycopg 3
* Pydantic, Pydantic Settings, HTTPX
* StoreKit 및 토큰 검증 경로를 위한 PyJWT, cryptography

---

## 정책 및 라이선스

* [개인정보 처리방침](./PRIVACY_POLICY.md)
* [서비스 이용약관](./TERMS_OF_SERVICE.md)
* [법적 고지](./LEGAL_NOTICE.md)
* [오픈소스 라이선스](./OPEN_SOURCE_LICENSES.md)
* [독점 라이선스](./LICENSE.md)

---

## 라이선스

Copyright (c) 2026 MFLab-AI. All rights reserved.

별도의 서면 라이선스가 없는 한 Memora의 소스 코드, 자산, 브랜드, 문서 및 관련 자료는 독점적으로 보호됩니다. 타사 오픈소스 구성요소는 각자의 라이선스를 따릅니다.
