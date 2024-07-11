# First stage: build the Go project
FROM golang:1.20-alpine as builder
WORKDIR /app
COPY . .
RUN go mod tidy
RUN go build -o kirito

# Second stage: create a small image for the binary
FROM alpine:latest
WORKDIR /root/
COPY --from=builder /app/kirito .
EXPOSE 8080
CMD ["./kirito"]
