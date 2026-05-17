# Memora (Re-Moment)

言語選択:
[English](./README.md) | [한국어](./README_KO.md) | [日本語](./README_JA.md) | [简体中文](./README_ZH.md) | [Español](./README_ES.md) | [Français](./README_FR.md) | [Português](./README_PT.md) | [हिन्दी](./README_HI.md) | [বাংলা](./README_BN.md) | [العربية](./README_AR.md)

---

[![Platform: iOS 18+](https://img.shields.io/badge/Platform-iOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ios/)
[![Platform: iPadOS 18+](https://img.shields.io/badge/Platform-iPadOS%2018%2B-blue.svg?style=flat-square&logo=apple)](https://developer.apple.com/ipados/)
[![Framework: Swift 6](https://img.shields.io/badge/Framework-Swift%206-orange.svg?style=flat-square&logo=swift)](https://developer.apple.com/swift/)
[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg?style=flat-square)](./LICENSE.md)

Memora、内部コード名 **Re-Moment** は、ユーザーの写真ライブラリをローカル優先で分析し、関連する瞬間を短いメモリーストーリー動画にまとめる iPhone/iPad アプリです。プライベートな写真インデックス作成、確認可能なおすすめ、編集可能なストーリー下書き、デバイス上でのレンダリングを中心に設計されています。Pro Vision AI は、より高品質なキャプションとリモート補助インデックス作成のための任意の有料機能です。

---

## 主な機能

### スマートストーリー推薦
* **写真ライブラリのインデックス作成:** PhotoKit で許可された写真を読み取り、日付、位置、 favorites、メディア種別、品質、顔の数、シーン、キャプション信号を抽出します。
* **推薦カード:** 同じ人物、似た背景、食べ物、季節、都市/旅行、時間スナップショット、意味のある瞬間、動画ハイライトなどからストーリー候補を作成します。
* **検索とメンテナンス:** インデックス済み写真をローカル検索でき、翻訳補完、整合性修復、推薦フィードバックのリセット、インデックス再開補助を提供します。

### 確認可能なメモリーストーリー
* **ストーリーレビュー:** レンダリング前に推薦ストーリーを確認し、写真の置換、削除、追加、並べ替えを行い、顔が明瞭な写真から代表人物を登録できます。
* **フィードバック制御:** 生成済みストーリーのアーカイブ、特定推薦の非表示、類似推薦タイプの除外、直近フィードバックの取り消しができます。
* **人物サポート:** 登録済み人物プロフィールは、人物中心のストーリー作成と今後の推薦品質改善に使われます。

### ローカル優先の Vision と保存
* **デフォルトはオンデバイス:** 標準インデックスとフォールバックキャプションは、ローカルの PhotoKit、Vision、メタデータ分析で処理されます。ユーザーが Pro Vision AI を有効にして使用しない限り、写真はサーバーへ送信されません。
* **ローカルデータベース:** インデックス、ストーリー、レンダー作業、設定、チェックポイント、人物プロフィールは SwiftData でアプリサンドボックスに保存されます。利用可能な場合、iCloud Drive ベースのデータベース保存も選択できます。
* **診断:** MetricKit 診断はクラッシュ、ハング、起動、CPU、ディスク書き込み問題の調査に使われます。診断にはユーザーの写真ファイルは含まれません。

### Pro Vision AI
* **任意の有料機能:** Pro Vision AI はサーバー側プロキシを使い、拡張 VLM キャプションとリモートインデックス処理量の管理を行います。処理量がない場合やサーバーに接続できない場合でも、アプリは標準のローカル Vision AI で利用できます。
* **サーバー側制御:** バックエンドは StoreKit 権限状態の検証、短期アクセストークンの発行、処理量管理、プロバイダー API キーの保護、冪等性、悪用防止信号の追跡を行います。
* **画像処理:** 画像ペイロードは要求されたキャプション処理のためだけに転送されます。サービスは元画像バイトを製品利用や AI 学習目的で保存しないよう設計されています。ただし、権限、処理量、デバッグ、セキュリティ、悪用防止のため、サニタイズ済みリクエストメタデータ、プロバイダー応答テキスト、リクエスト状態、処理量カウンター、デバイスハッシュ、エラー情報などの運用記録を保持する場合があります。

### 動画レンダリングと保存
* **ネイティブレンダラー:** メモリーストーリーは、キャッシュされた写真アセットをもとに AVFoundation で標準 30fps を目標としてレンダリングされ、dissolve、slide、wipe、zoom 系の動きとトランジションを使用します。
* **Photos への書き出し:** レンダリング前に iCloud 専用アセットのローカルコピーを準備し、完成動画は Photos add-only 権限と Photos 互換 MOV fallback 経路で保存します。
* **進行状況とキャンセル:** ダウンロード、レンダリング、保存、失敗、キャンセル、復旧状態をアプリで表示します。

---

## 重要な注意事項

* Memora はストーリー推薦のために写真読み取り権限を必要とします。限定アクセスにも対応しますが、意図した体験にはフルアクセスが適しています。
* レンダリング済み動画を写真アプリに保存するには、写真追加権限が必要です。
* Pro Vision AI は選択された画像データをバックエンドと設定済み VLM プロバイダーへ送信します。リモート処理してよい写真にのみ使用してください。
* AI 生成のキャプションや推薦は不正確な場合があります。レンダリングまたは共有する前に内容を確認してください。
* iCloud Drive データベース保存は、ユーザーの Apple iCloud 設定とデバイス状態に依存します。
* 商品名、処理量、価格、対応プラットフォームは App Store リリース前後で変更される場合があります。

---

## 技術スタック

### クライアント
* Swift 6, SwiftUI, SwiftData
* PhotoKit, Vision, AVFoundation, MetricKit
* MLX Swift LM / MLX VLM 関連パッケージ, Swift HuggingFace, Swift Transformers

### サーバー
* FastAPI, Uvicorn, Starlette
* PostgreSQL, SQLAlchemy, Alembic, Psycopg 3
* Pydantic, Pydantic Settings, HTTPX
* StoreKit とトークン検証経路のための PyJWT, cryptography

---

## ポリシーとライセンス

* [Privacy Policy](./PRIVACY_POLICY.md)
* [Terms of Service](./TERMS_OF_SERVICE.md)
* [Legal Notice](./LEGAL_NOTICE.md)
* [Open Source Licenses](./OPEN_SOURCE_LICENSES.md)
* [Proprietary License](./LICENSE.md)

---

## ライセンス

Copyright (c) 2026 MFLab-AI. All rights reserved.

別途書面によるライセンスがない限り、Memora のソースコード、アセット、ブランド、文書、および関連資料は proprietary として保護されます。サードパーティのオープンソース構成要素は、それぞれのライセンスに従います。
