# My Project Portfolio

[![Frontend CI](https://github.com/YukiYonekura-321/frontend/actions/workflows/ci.yml/badge.svg)](https://github.com/YukiYonekura-321/frontend/actions/workflows/ci.yml)
[![Backend CI](https://github.com/YukiYonekura-321/backend/actions/workflows/ci.yml/badge.svg)](https://github.com/YukiYonekura-321/backend/actions/workflows/ci.yml)
[![Coverage](https://codecov.io/gh/YukiYonekura-321/portfolio/branch/main/graph/badge.svg)](https://codecov.io/gh/YukiYonekura-321/portfolio)
[Live Preview](https://<vercel-preview>)

## 概要
- フルスタック CRUD アプリ（Rails API + Next.js）。Firebase Auth と OpenAI を組み込んだポートフォリオプロジェクトです。
- 目的: 採用ポートフォリオ / テスト・CI・デプロイの実装経験を示す

## リポジトリ
- Frontend (Next.js): https://github.com/YukiYonekura-321/frontend
- Backend (Rails API): https://github.com/YukiYonekura-321/backend

## アーキテクチャ（簡易図）
```mermaid
flowchart LR
  N[Next.js (frontend)]
  R[Rails API (backend)]
  DB[(Postgres)]
  Firebase[(Firebase Auth)]
  OpenAI[(OpenAI API)]

  N -->|HTTP API| R
  R --> DB
  N -->|Auth| Firebase
  R -->|Calls| OpenAI
```

## 注目してほしい箇所（採用担当者向け）
- Frontend: `/components/PostEditor`（生成UI）, `/e2e`（Playwright シナリオ）
- Backend: `app/services/openai_service.rb`（生成ロジック）, `spec/requests/posts_spec.rb`（主要 API テスト）
- CI: `.github/workflows/ci.yml`（unit + integration + E2E を実行）

## テストと CI（要約）
- テスト方針: テストピラミッドに従い、ユニット > 統合 > E2E（重要フローのみ）
- E2E: Playwright を使用（主要フロー: 認証 / 投稿 CRUD / 生成AI フロー）
- CI: GitHub Actions で PR ごとに自動実行、結果は上記バッジに反映

## ローカルで全体を起動する（開発者向け）
1. backend を起動
   - `git clone https://github.com/YukiYonekura-321/backend`
   - `cp .env.example .env` (環境変数を設定)
   - `bundle install && rails db:setup && rails s -p 3001`
2. frontend を起動
   - `git clone https://github.com/YukiYonekura-321/frontend`
   - `cp .env.example .env` (BACKEND_URL=http://localhost:3001 を設定)
   - `yarn install && yarn dev -p 3000`
3. E2E を実行
   - (frontend 側) `npx playwright test`

## 何を見てほしいか（採用時の指示）
- まず portfolio のこの README を見て全体像を把握してください
- フロントとバックの注目ファイルを上記から見てください
- CI が回っていること（バッジ）と Pull Request の単位でのテストを確認していただけると嬉しいです

## スクリーンショット / 動作デモ
- `/docs` に短い GIF やスクリーンショットを置いています（例: `docs/demo.gif`）