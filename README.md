# Ubuntu日本語環境（Docker）

Ubuntu日本語環境をDockerで構築します。  
学習目的の環境のため、ホストとコンテナ内のworkディレクトリを同期しています。  
必要に応じて設定を変更してご利用ください。  

## 動作環境

- OS: `Windows` or `macOS`
- インストール: `Docker Desktop`

## 導入方法

ZIPをダウンロードし、任意の場所に展開してください。  

[ZIPダウンロード](https://github.com/seiya0-g/docker-ubuntu-jp/archive/refs/heads/main.zip)  

- 参考
  - [`ソース コード アーカイブのダウンロード - GitHub Docs`](https://docs.github.com/ja/repositories/working-with-files/using-files/downloading-source-code-archives)

## 環境構築

ターミナル（WindowsではPowershell、GitBash等）でコマンドを打ち、環境を構築します。  

### docker-compose

- `docker-compose.yml`があるディレクトリで、`docker-compose up -d` コマンドを実行してください。

```bash
# ターミナルで実行
## ls コマンドで docker-compose.yml があるか確認
ls docker-compose.yml
## docker-compose で環境構築  ※ 時間がかかるので注意
docker-compose up -d
```

- 参考
  - [`Compose ファイル リファレンス — Docker-docs-ja 24.0 ドキュメント`](https://docs.docker.jp/reference/compose-file/toc.html)

### 確認

- `docker exec -it <container-name> bash` コマンドでコンテナ（Ubuntuサーバー）に入ります。  
  （プロジェクト名を変更していなければ、コンテナ名は `docker-ubuntu-jp-container` になります）

```bash
# ターミナルで実行
## Ubuntuサーバーに入る
docker exec -it docker-ubuntu-jp-container bash
```

上記のコマンドを実行すると、下記のような表示になります。

```bash
$ # 実行例
$ docker exec -it docker-ubuntu-jp-container bash
root@docker-ubuntu-jp-host:/mnt/work# 
```

試しに新規ファイルを作ってみましょう。  
`touch test.txt` のコマンドを実行すると、空の`test.txt`ファイルが生成できます。  

```bash
root@docker-ubuntu-jp-host:/mnt/work# touch test.txt
root@docker-ubuntu-jp-host:/mnt/work# ls
README.md  test.txt
root@docker-ubuntu-jp-host:/mnt/work# 
```

- 参考
  - [`docker exec — Docker-docs-ja 24.0 ドキュメント`](https://docs.docker.jp/engine/reference/commandline/exec.html)

## 解説

### Docker 環境ファイル

[.env](./.env) ファイルはDockerの環境ファイルです。  

- 参考
  - [`ファイルでデフォルトの環境変数を設定 — Docker-docs-ja 24.0 ドキュメント`](https://docs.docker.jp/compose/env-file.html)
  - [`Compose CLI 環境変数 — Docker-docs-ja 24.0 ドキュメント - COMPOSE_PROJECT_NAME`](https://docs.docker.jp/compose/reference/envvars.html#compose-project-name)

### Docker バインドマウント

ローカルの [work/](./work/) フォルダとコンテナ内の`/mnt/work`ディレクトリが同期しており、  
[work/](./work/) にファイルやフォルダを格納すると、コンテナ内のディレクトリにも格納されます。

- 参考
  - [`バインド マウント(bind mount) の使用 — Docker-docs-ja 24.0 ドキュメント - compose でバインドマウントを使用`](https://docs.docker.jp/storage/bind-mounts.html#compose)

## 参考ページ

- [`GitHub Docs`](https://docs.github.com/ja)
  - [`ソース コード アーカイブのダウンロード - GitHub Docs`](https://docs.github.com/ja/repositories/working-with-files/using-files/downloading-source-code-archives)
  - [`テンプレートからリポジトリを作成する - GitHub Docs`](https://docs.github.com/ja/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)
  - [`リポジトリをクローンする - GitHub Docs`](https://docs.github.com/ja/repositories/creating-and-managing-repositories/cloning-a-repository)
- [`Docker ドキュメント日本語化プロジェクト — Docker-docs-ja 24.0 ドキュメント`](https://docs.docker.jp/)
  - [`ファイルでデフォルトの環境変数を設定 — Docker-docs-ja 24.0 ドキュメント`](https://docs.docker.jp/compose/env-file.html)
  - [`Compose CLI 環境変数 — Docker-docs-ja 24.0 ドキュメント - COMPOSE_PROJECT_NAME`](https://docs.docker.jp/compose/reference/envvars.html#compose-project-name)
  - [`Dockerfile リファレンス — Docker-docs-ja 24.0 ドキュメント`](https://docs.docker.jp/engine/reference/builder.html)
  - [`Compose ファイル リファレンス — Docker-docs-ja 24.0 ドキュメント`](https://docs.docker.jp/reference/compose-file/toc.html)
  - [`バインド マウント(bind mount) の使用 — Docker-docs-ja 24.0 ドキュメント - compose でバインドマウントを使用`](https://docs.docker.jp/storage/bind-mounts.html#compose)
  - [`docker exec — Docker-docs-ja 24.0 ドキュメント`](https://docs.docker.jp/engine/reference/commandline/exec.html)
- [`Docker Hub Container Image Library - App Containerization`](https://hub.docker.com/)
  - [`ubuntu - Official Image - Docker Hub`](https://hub.docker.com/_/ubuntu)
