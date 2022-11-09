FROM golang:latest AS build
RUN apk --no-cache add gcc g++ make git
WORKDIR /go/src/app
COPY main.go .
ENV GO111MODULE="on"
RUN go mod tidy
RUN GOOS=linux go build -ldflags="-s -w" -o ./bin/backend

FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /usr/bin
COPY --from=build /go/src/app/bin /go/bin
EXPOSE 8081
ENTRYPOINT /go/bin/backend --port 8081