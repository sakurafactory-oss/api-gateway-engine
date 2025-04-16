# api-gateway-engine

**軽量・高速・拡張性を備えたAPIゲートウェイエンジン（UIレス・API駆動）**  
REST APIでルーティング・認証・レート制限を柔軟に制御でき、スモールスタートから拡張まで対応可能なGo製プロキシ基盤です。

---

## 特徴

- Go言語による高速・シンプルな実装
- 設定やルーティングルールをすべてREST APIで操作可能
- APIキー認証とレート制限機能を内蔵
- UIレスでサーバー用途に最適、軽量構成
- SQLiteまたはJSONファイルで永続化
- 単体バイナリまたはDockerで簡単に運用開始可能

---

## 実装済み機能

- [x] ルート定義に基づくHTTPリバースプロキシ
- [x] APIキーによるアクセス制御（ルート単位で指定可能）
- [x] 時間単位のレート制限機能
- [x] 管理用REST API（ルート・キー管理）
- [x] ヘルスチェックエンドポイント（`/healthz`）

---

## 今後の予定機能

- [ ] モニタリング対応（Prometheus等）
- [ ] API定義用のドキュメントエンドポイント
- [ ] Webベースの設定UI（React or Svelte）
- [ ] トークンベース認証（JWT等）
- [ ] 外部クラウドサービスとの自動統合

---

## ディレクトリ構成（予定）

api-gateway-engine/
├── cmd/               # main.go
├── router/            # プロキシと管理APIルーティング
├── middleware/        # 認証・レート制限
├── storage/           # SQLite or JSONベースのデータ管理
├── config/            # 初期設定ファイル
└── go.mod / go.sum

---

## 起動方法（開発用）

```bash
# 依存インストール
go mod tidy

# 起動
go run cmd/main.go



⸻

管理用API例

ルート登録

POST /admin/routes
Content-Type: application/json

{
  "path": "/api/v1/hello",
  "target": "http://localhost:9000/hello",
  "apikey_required": true,
  "rate_limit": 20
}

APIキー登録

POST /admin/keys
Content-Type: application/json

{
  "key": "abcd1234",
  "description": "test key"
}



⸻

ライセンス

MIT License

⸻

コントリビューションについて

アイデア・不具合報告・改善提案など歓迎しています。
このプロジェクトはシンプルかつ実用的なAPIゲートウェイを目指して継続開発中です。
