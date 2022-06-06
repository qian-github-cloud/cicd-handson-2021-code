#build
FROM golang:1.17.1 as builder

WORKDIR /app

COPY .  ./

RUN CGO_ENABLE=0 go build -o ./server-run ./server

# deploy
FROM scratch

EXPOSE 9090

COPY --from=builder app/server-run /.
COPY web /web

cmd ["./server-run"]