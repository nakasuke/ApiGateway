
# MCP対応マイクロサービス・ゲートウェイ設計ドキュメント

## 1. 目的と背景
本ドキュメントは、Python + Flask で実装されたマイクロサービスを統合管理する
ゲートウェイの設計を記述する。
本ゲートウェイは将来的に MCP（Model Context Protocol）Server へ移行することを前提とする。

## 2. 設計方針
- 1サービス = 1 MCPツール
- 設定は MCPリソースとして扱う
- 並列実行は「系統（Service Line）」で管理する
- 系統数はソリューションに含める
- 実行時一時設定（ephemeral setting）は導入しない
- MCPリソースは content を直接返す

## 3. 用語定義
### ソリューション（Solution）
使用可能な MCPツール、各ツールの系統数、系統ごとの MCPリソースを定義した静的な構成。

### コンテキスト（Context）
ソリューションに基づいて生成される 1 回の実行状態。

### MCPツール（MCP Tool）
実行ロジックを提供する単位。1 サービス = 1 MCPツール。

### 系統（Service Line）
MCPツールを並列実行するための事前定義された実行枠。

### MCPリソース（MCP Resource）
MCPツールが参照する設定ファイル。

## 4. 全体構造
Solution
 ├─ MCP Tool
 │   ├─ Line 1 (Resource)
 │   └─ Line 2 (Resource)

## 5. ユースケース概要
- ソリューション一覧取得
- MCPツール・系統状態取得
- MCPリソース登録・取得
- コンテキスト生成・終了

## 6. MCP対応
本設計は MCP Server への移行を容易にする。
