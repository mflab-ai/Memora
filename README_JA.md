# Memora (Re-Moment)

🌐 **Select Language / 언어 선택:**
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: macOS 15+](https://img.shields.io/badge/Platform-macOS%2015%2B-lightgrey.svg?style=flat-square&logo=apple)](https://developer.apple.com/macos/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE)

Memora（内部プロジェクトコード名 **Re-Moment**）は、プライバシーを最優先にしたオンデバイスAI搭載のスマートストーリーコレクションおよび写真スライドショー作成アプリです。ユーザー個人のデリケートな写真資産やメタデータに対する完全な統制権を維持しながら、AIが自動的にテーマ別にグループ化し、美しいナラティブキャプションを作成し、映画のようなスライドショービデオをレン더リングする革新的な体験を提供します。

---

## 📸 主な機能 (Core Features)

### 🧠 時空間ベースのスマートコレクション (Spatio-Temporal Smart Collections)
* **クラスタリングおよび推奨エンジン:** 高度な空間的（地理的位置）および時間的（時間間隔）しきい値アルゴリズムを適用し、ユーザーの写真資産を一つのまとまりがあり文脈のあるイベント（例：*"パリでの週末"*, *"夏のピクニック"*）に自動的にグループ化します。
* **テーマの多角化:** ユーザーの好み、写真固有のメタデータ、および視覚的特徴を組み合わせて、インテリジェントで構造化されたコレクションシグナルとサマリーカードを生成します。

### 🛡️ プライバシーファースト・オンデバイスビ전AI (On-Device Vision AI)
* **ゼロナレッジ・インデックス作成 (Zero-Knowledge Indexing):** アップルの **CoreML**、**Vision**、およびローカルLLM/VLMランナー（**MLX Swift / MLX Swift LM / MLX VLM**）を活用し、写真の分析、インデックス作成、顔認識などのコア処理を外部サーバーに送信することなく、100%デバイス内だけで独立して実行します。
* **ローカル安全メタデータ保管:** 生成された説明文、キャプション、およびスマート分析ログは、デバイス内部の安全なサンドボックスにローカルに保存されるか、ユーザーが有効にした個人の **Apple iCloud** アカウントを介して安全に同期されます。

### ⚡ プロ・ビジョンAI (Pro Vision AI - クラウド連携VLM)
* **高精度キャプション生成:** 高度な視覚言語モデル（VLM）を活用して、豊かで文脈把握に優れたキャプションと精密なタグを生成するプレミアムオプション機能です。
* **インメモリ無記録処理ポリシー (In-Memory Zero-Retention Policy):** 送信された画像は一時的に揮発性メモリ（RAM）上でのみ処理され、キャプションが生成された直後に**サーバーから100%永久に削除**されます。画像の保存、ログ記録、またはモデルの学習に活用されることは一切ありません。

### 🎬 映画のような写真スライドショービデオのレンダリング (Slideshow Rendering)
* **動的トランジションエンジン:** 精密に調整された特殊効果（*クロスディゾルブ、プッシュ、ワイプ、ズーム、ケン・バーンズ効果*など）を適用し、写真ストーリーをプロのドキュメンタリーレベルのシネマティック動画に織り上げます。
* **PhotoKitネイティブ連携:** アップルの **PhotoKit** および **AVFoundation** に基づいて開発され、iOSおよびmacOSハードウェアで直接最大60fpsの滑らかで鮮明な高解像度ビデオをレンダリングします。

---

## 🔒 プライバシーおよびデータセキュリティ公約 (Privacy & Data Security Commitment)

Memoraは、ユーザーのデータ主権（Data Sovereignty）の守護という厳格な原則の下で設計されています。当社は、ユーザーの大切な写真情報に対して絶対的な機密保持とセキュリティを保証します。

> [!IMPORTANT]
> * **サーバー保存の完全排除 (Zero Server-Side Storage):** オプション機能である「Pro Vision AI」のために当社サーバーに送信されたすべての写真は、一時的な揮発性メモリ（RAM）内でのみ一時的に処理されます。ユーザー写真は、いかなる場合もディスクに記録されず、データベースに保存されたりキャッシュされたり、サーバーログに残されることはありません。
> * **AIモデルの学習・開発使用の全面禁止 (No AI Model Training):** 当社は、人工知能開発に対する徹底した無使用ポリシー（Zero-Use Policy）に従います。ユーザーの写真、生成された説明文、および個人メタデータは、大規模言語モデル（LLM）、視覚言語モデル（VLM）、またはいかなるAIモデルの学習およびファインチューニング（Fine-Tuning）用途にも**絶対に利用されません。**
> * **即時のRAM破壊 (Instant RAM Destruction):** プロキシサーバーがユーザーデバイスに生成されたキャプションテキストを返して伝達するその瞬間、RAMに常駐していたすべての画像バイトデータは**直ちに、かつ完全に破壊・削除**されます。
> * **オンデバイスのデフォルト動作 (On-Device Default):** 写真のグループ化、ローカルインデックス作成、顔認識、スライドショービデオのレンダリングなど、アプリのすべての基盤機能は100%ローカルデバイス内で動作します。ユーザーがプロ・ビジョンAIを明示的に有効にしない限り、ネットワークを通じた画像送信は一切発生しません。

---

## 🛠️ 技術スタック (Technology Stack)

### クライアント (iOS / macOS)
* **言語およびフレームワーク:** Swift 6, SwiftUI, SwiftData, CoreML, Vision, AVFoundation, PhotoKit
* **オンデバイスAIエコシステム:** `mlx-swift`, `mlx-swift-lm`, `swift-huggingface`, `swift-transformers`
* **高性能およびネットワークユーティリティ:** `yyjson` (超高速JSONパーサー), `EventSource` (SSEストリーミングAPIハンドラー), `swift-jinja` (テンプレートレンダラー)

### サーバー (Python Backend Proxy)
* **APIゲートウェイおよびコア:** FastAPI, Uvicorn, Starlette, Pydantic & Pydantic Settings
* **データベースおよびマイグレーション:** PostgreSQL, SQLAlchemy (ORM), Alembic, Psycopg 3
* **暗号化および検証:** `cryptography` (アップルApp Store API署名確認), `PyJWT` (JWSトークン処理)

---

## ⚖️ 諸ポリシーおよびライセンス (Policies & Licensing)

より具体的で詳細な法的告知および方針については、以下のドキュメントを参照してください。

* 📄 **[個人情報保護方針 (Privacy Policy)](./PRIVACY_POLICY.md)** – ゼロデータサーバー無保存原則、オンデバイスローカル保管、安全なiCloud同期に関する総括的な仕様。
* 📄 **[サービス利用規約 (Terms of Service)](./TERMS_OF_SERVICE.md)** – モバイルアプリケーションの使用規定、Apple App Storeを介したアプリ内課金（IAP）、およびプロ・ビジョンAI使用クォータポリシー。
* 📄 **[法的告知 (Legal Notice)](./LEGAL_NOTICE.md)** – 開発者情報（MFLab-AI / 金相勲）、知的財産権宣言およびサービス責任限界の告知。
* 📄 **[オープンソースライセンス (Open Source Licenses)](./OPEN_SOURCE_LICENSES.md)** – クライアントおよびサーバープログラムに搭載されているすべてのサードパーティ製オープンソースライブラリのリストとライセンスの告知。

---

## 🛡️ 著作権およびライセンス (License)

Copyright (c) 2026 MFLab-AI. All rights reserved.

本リポジトリ内のすべてのソースコード、アセット、および関連ドキュメントは、**MFLab-AI**の固有の資産です。本リポジトリは、情報提供、規制準拠の検討、および技術デモの目的のみに維持管理されます。MFLab-AIの事前の明示的な書面による同意なしに、本ソフトウェアを複製、配布、修正、または使用することは厳格に禁止されています。
