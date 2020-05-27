FROM golang:1-alpine as builder

RUN apk --update upgrade \
&& apk --no-cache --no-progress add git make gcc musl-dev \
&& rm -rf /var/cache/apk/*

RUN go get github.com/emersion/hydroxide/cmd/hydroxide

FROM alpine:3.9 as base
RUN apk --update upgrade \
    && apk --no-cache --no-progress add ca-certificates git \
    && rm -rf /var/cache/apk/*

EXPOSE 1025

COPY --from=builder /go/bin/hydroxide /usr/bin/hydroxide

ENTRYPOINT ["/usr/bin/hydroxide"]
