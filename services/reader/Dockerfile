FROM golang:alpine AS builder

WORKDIR /go/src/github.com/PicPay/picpay-jr-devops-challenge/services/go

COPY . /go/src/github.com/PicPay/picpay-jr-devops-challenge/services/go

RUN go mod download

RUN go build -o main .

FROM alpine

WORKDIR /app

COPY --from=builder /go/src/github.com/PicPay/picpay-jr-devops-challenge/services/go .

EXPOSE 8080

CMD ["./main"]