# syntax=docker/dockerfile:1

ARG VERSION
FROM --platform=${BUILDPLATFORM} caddy:${VERSION}-builder AS builder

ARG TARGETPLATFORM
ARG BUILDPLATFORM
ARG TARGETOS
ARG TARGETARCH

RUN GOOS=${TARGETOS} GOARCH=${TARGETARCH} xcaddy build \
    --with github.com/caddy-dns/cloudflare

FROM --platform=${TARGETPLATFORM} caddy:${VERSION}

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
