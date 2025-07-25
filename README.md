# my-llm-app

AWS Lambda + Amazon Bedrock を用いたリアルタイム生成 AI チャットアプリケーション

## 概要

コストを抑えた個人開発向けの生成 AI チャットアプリケーションです。
AWS 無料枠を最大限活用し、月額$2-3 程度で運用可能な設計となっています。

## 主な機能

- 🚀 リアルタイムチャット（WebSocket）
- 💾 チャット履歴保存（DynamoDB）
- 🤖 Claude 3.7 Sonnet / Sonnet 4 対応
- 💰 低コスト設計（AWS 無料枠活用）
- 🔒 最小限のセキュリティ実装

## 技術スタック

- **インフラ**: AWS CloudFormation
- **バックエンド**: AWS Lambda (Python)
- **フロントエンド**: HTML5 + Vanilla JavaScript
- **データベース**: Amazon DynamoDB
- **AI**: Amazon Bedrock (Claude 3.7 Sonnet)

## プロジェクト構成

```
my-llm-app/
├── documents/          # 設計書・ドキュメント
├── src/               # Lambda関数ソースコード
├── lambda/            # Lambdaデプロイ用パッケージ
├── frontend/          # Web UI
├── cloudformation/    # インフラ定義
└── README.md         # このファイル
```

## クイックスタート

### 前提条件

- AWS CLI が設定済みであること
- Node.js 14 以上がインストールされていること
- Python 3.9 以上がインストールされていること

### 1. リポジトリクローン

```bash
git clone [repository-url]
cd my-llm-app
```

### 2. デプロイ

```bash
# CloudFormationスタックのデプロイ
aws cloudformation deploy \
  --template-file cloudformation/template.yaml \
  --stack-name my-llm-app \
  --capabilities CAPABILITY_IAM

# フロントエンドのビルド・デプロイ
cd frontend
npm run build  # または手動でS3にアップロード
```

### 3. 動作確認

デプロイ完了後、CloudFormation の出力から URL を取得してアクセス

## 開発ガイド

### ローカル開発

```bash
# Lambda関数のローカルテスト
cd src
python -m pytest tests/

# フロントエンドのローカル開発
cd frontend
python -m http.server 8000
```

### デプロイ手順

詳細なデプロイ手順は `documents/DEPLOYMENT_GUIDE.md` を参照

## コスト見積もり

- **AWS インフラ**: 月額$2-3（個人利用想定）
- **Bedrock 使用料**: 月$5-10（使用量に依存）

## トラブルシューティング

よくある問題と解決方法は `documents/TROUBLESHOOTING.md` を参照

## ライセンス

MIT License

## 貢献

プルリクエストは歓迎します！大きな変更の場合は、まずイシューを作成してください。
