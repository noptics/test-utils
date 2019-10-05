from ubuntu as builder

RUN apt update && apt install unzip wget -y

RUN mkdir -p /stan

WORKDIR /stan

RUN wget https://github.com/nats-io/nats-streaming-server/releases/download/v0.16.2/nats-streaming-server-v0.16.2-linux-amd64.zip

RUN unzip nats-streaming-server-v0.16.2-linux-amd64.zip

FROM alpine

RUN apk add --no-cache curl bash ca-certificates

COPY --from=builder /stan/nats-streaming-server-v0.16.2-linux-amd64/nats-streaming-server /nats-streaming-server

EXPOSE 4222

RUN chmod +x /nats-streaming-server

CMD ["/nats-streaming-server"]