
# MCP対応マイクロサービス・ゲートウェイ

本リポジトリは、Python + Flask で実装されたマイクロサービスを統合管理する
**MCP（Model Context Protocol）対応ゲートウェイ**の設計・仕様をまとめたものです。

## 目的
- マイクロサービスを **MCPツール** として統一的に扱う
- 設定ファイルを **MCPリソース** として管理する
- 並列実行は **系統（Service Line）** により安全に制御する
- 将来的な MCP Server 化を容易にする

## ドキュメント構成

```
docs/
├─ architecture.md        # 最上位設計ドキュメント（本設計の正）
├─ openapi.yaml           # ゲートウェイAPI最終仕様（OpenAPI）
├─ solution.schema.yaml   # solution.yaml の正式仕様
└─ glossary.md            # 用語集
```

## 基本ルール

- **architecture.md を最上位設計**とする
- API仕様は **openapi.yaml を正**とする
- 実装は本設計・仕様に準拠すること

## 設計の要点（抜粋）

- 1サービス = 1 MCPツール
- 設定は MCPリソースとして content を直接返却
- 並列実行は系統で管理（設定の競合を防止）
- ソリューションは構成定義、コンテキストは実行状態

## 想定読者

- ゲートウェイ実装担当者
- MCP Server 化を検討する設計者
- 運用・保守担当者

## 次のステップ

- Flask 実装スケルトン作成
- solution.yaml ローダ・バリデータ実装
- コンテキスト／系統管理ロジック実装
