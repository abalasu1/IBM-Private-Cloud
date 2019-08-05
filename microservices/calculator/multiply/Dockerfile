FROM golang:alpine AS build-env
MKDIR /app
WORKDIR /app
ADD main.go /app
RUN cd /app && go build -o goapp

FROM alpine
RUN apk update && apk add ca-certificates && \
    update-ca-certificates && rm -rf /var/cache/apk/*

WORKDIR /app
COPY --from=build-env /app/goapp /app

EXPOSE 80
ENTRYPOINT ./goapp
