# Docker Rails Templates

このリポジトリには、様々なOSとバージョン上でRailsアプリケーションを実行するためのDockerfileテンプレートが含まれています。各テンプレートは、特定のRailsバージョン、OS、データベースの組み合わせに最適化されています。

## プロジェクト構成

このプロジェクトは以下の構造で組織されています：

```
docker-rails-templates/
├── rails-[version]/
│   ├── [os]/
│   │   ├── [os-version]/
│   │   │   ├── [database]/
│   │   │   │   └── Dockerfile
```

例えば：

```
docker-rails-templates/rails-7.0/ubuntu/22.04/postgresql/Dockerfile
```

## サポートされている組み合わせ

### Railsバージョン

- Rails 6.1 (Ruby 3.0)
- Rails 7.0 (Ruby 3.0)
- Rails 7.1 (Ruby 3.2)
- Rails 7.2 (Ruby 3.3)
- Rails 8.0 (Ruby 3.3)

### OS

- Ubuntu (20.04, 22.04)
- Amazon Linux (2, 2023)
- Alpine Linux (3.16, 3.18)
- CentOS (7, Stream 9)

### データベース

- PostgreSQL
- MySQL
- SQLite

## 使用方法

1. 必要なRailsバージョン、OS、データベースに対応するDockerfileを選択します。
2. Dockerfileをプロジェクトのルートディレクトリにコピーします。
3. 必要に応じてDockerfileをカスタマイズします。
4. 以下のコマンドでDockerイメージをビルドします：

```bash
docker build -t my-rails-app .
```

5. 以下のコマンドでコンテナを実行します：

```bash
docker run -p 3000:3000 my-rails-app
```

## 注意事項

- これらのDockerfileは開発環境用に最適化されています。
- フロントエンド環境（Node.js、Yarn等）は含まれていません。必要に応じて追加してください。
- これらのDockerfileはRails自体のインストールは行わず、Railsが動作するための環境のみを提供します。
- データベースサーバー自体は含まれていません。必要に応じて別のコンテナで実行するか、docker-composeを使用してリンクしてください。

## 貢献

バグの報告や改善の提案は、Issueやプルリクエストでお気軽にどうぞ。


