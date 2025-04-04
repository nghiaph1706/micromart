FROM golang:1.16-alpine

WORKDIR /app
COPY . .

RUN go mod tidy
RUN go build -o payment-service .

EXPOSE 8080
CMD ["./payment-service"]