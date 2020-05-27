FROM golang:1-alpine as builder

RUN apk --update upgrade \
&& apk --no-cache --no-progress add git make gcc musl-dev \
&& rm -rf /var/cache/apk/*

RUN go get github.com/emersion/hydroxide/cmd/hydroxide

FROM alpine:3.9
RUN apk --update upgrade \
    && apk --no-cache --no-progress add ca-certificates git \
    && rm -rf /var/cache/apk/*

EXPOSE 1025

COPY --from=builder /go/bin/hydroxide /usr/bin/hydroxide
USER 1000:1000
ENTRYPOINT ["/usr/bin/hydroxide smtp"]
