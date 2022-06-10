VERSION 0.6
FROM golang:1.18-alpine
WORKDIR /workspace

RUN apk add --no-cache make git gcc musl-dev

setVersion:
  ARG APPVERSION=dev
  RUN echo -n $APPVERSION > /version.txt
  SAVE ARTIFACT /version.txt

DEPS:
  COMMAND
  COPY go.mod go.sum ./
  RUN go mod download
  # Output these back in case go mod download changes them.
  SAVE ARTIFACT go.mod AS LOCAL go.mod
  SAVE ARTIFACT go.sum AS LOCAL go.sum

