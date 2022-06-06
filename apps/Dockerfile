# ベースイメージをbuilderイメージとして指定
FROM golang:1.17 as builder

# ワークディレクトリを指定
WORKDIR /app

# ホストOSのapps内全てをWORKDIRにコピー
COPY . ./

# [編集] ビルド
RUN CGO_ENABLED=0 go build -o ./server-run ./server

# [編集] scratchイメージを指定
FROM scratch

# コンテナのポートを9090で公開
EXPOSE 9090

# [追加] golang:1.16でビルドしたアプリケーションをコピー
COPY --from=builder app/server-run /.
COPY web /web

# アプリ実行
CMD [ "./server-run" ]