# Nginx Load Balancer with Docker for Ethereum
このプロジェクトは、DockerとNginxを使用してEthereumのNode(EC/CC)用のロードバランサーを構築するためのものです。

## 前提条件

- Docker
- Docker Compose

## セットアップ

1. このリポジトリをクローンします：
2. `.env`ファイルを作成し、以下の環境変数を設定します：
```sh
cp .envsample .env
```
```sh
NGINX_PORT=80
BACKEND_SERVER1=<backend-server-1-ip>:<port>
BACKEND_SERVER2=<backend-server-2-ip>:<port>
BACKEND_SERVER3=<backend-server-3-ip>:<port>
```
注: `<backend-server-1-ip>`と`<backend-server-2-ip>`と`<backend-server-3-ip>`を実際のバックエンドサーバーのIPアドレスに、`<port>`を対応するポート番号に置き換えてください。

3. `nginx/nginx.conf`ファイルを必要に応じて編集します。

## 使用方法
1. Docker Composeを使用してサービスを起動します：
```sh
docker-compose up -d
```

2. ブラウザで`http://localhost:<NGINX_PORT>`にアクセスして、ロードバランサーが機能していることを確認します。

## 設定の変更

- Nginxの設定を変更する場合は、`nginx/nginx.conf`ファイルを編集し、Dockerコンテナを再起動してください。
- バックエンドサーバーの設定を変更する場合は、`.env`ファイルを編集し、Dockerコンテナを再起動してください。

## 注意点
- 現時点では、Geth/Prysmのペアのみサポートしています

## トラブルシューティング

- 502 Bad Gatewayエラーが発生した場合：
- バックエンドサーバーが起動していることを確認してください。
- `.env`ファイルのバックエンドサーバーのIPアドレスとポート番号が正しいことを確認してください。
- Dockerネットワークの設定を確認してください。

## ファイル構造
.  
├── .env  
├── .gitignore  
├── compose.yaml  
├── nginx  
│   └── nginx.conf  
└── README.md  

