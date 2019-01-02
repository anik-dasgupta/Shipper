# vessel-service/Dockerfile
FROM golang:1.9.0 as builder

WORKDIR /go/src/github.com/EwanValentine/shippy/vessel-service

COPY . .

RUN go get -d ./...

RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo .


FROM debian:latest

RUN mkdir /app
WORKDIR /app
COPY --from=builder /go/src/github.com/EwanValentine/shippy/vessel-service/vessel-service .

CMD ["./vessel-service"]