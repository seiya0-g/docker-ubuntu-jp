FROM ubuntu:22.04

# コマンド実行
## パッケージリスト更新
RUN apt-get update \
    ## パッケージインストール
    && apt-get install -y --no-install-recommends \
    ### vi
    vim \
    ### TZ(タイムゾーン)データ
    tzdata \
    ### 日本語言語パック
    language-pack-ja \
    ## パッケージキャッシュ削除
    && apt-get -y clean

# 環境変数設定
## タイムゾーン設定（日本）
ENV TZ Asia/Tokyo
## 言語設定（日本）
ENV LANG ja_JP.utf8

# 作業ディレクトリ作成
WORKDIR /mnt/work/
