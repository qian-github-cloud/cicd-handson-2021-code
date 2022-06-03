FROM golang:1.17.1

WORKDIR /app

COPY .  ./

RUN go build -o ./server-run ./server

EXPOSE 9090

cmd ["./server-run"]