FROM golang:1.12.5 AS builder
WORKDIR /go/src/github.com/khakharis/href-counter/
RUN go get -d -v golang.org/x/net/html
COPY app.go .
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .

FROM alpine:3.9
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=builder /go/src/github.com/khakharis/href-counter/app .
CMD ["./app"]