# Custom telemetrygen image with shell capabilities for e2e testing
# This enables container ID detection from Kubernetes API for proper association testing

FROM alpine:latest@sha256:28bd5fe8b56d1bd048e5babf5b10710ebe0bae67db86916198a6eec434943f8b as base

FROM ghcr.io/open-telemetry/opentelemetry-collector-contrib/telemetrygen:latest@sha256:8ff794579e6f152ef7f971c4666b3c9df853a241186cc168429620c318e58e82 as telemetrygen-source

FROM base

RUN apk add --no-cache curl

COPY --from=telemetrygen-source /telemetrygen /telemetrygen
ARG USER_UID=10001
ARG USER_GID=10001
USER ${USER_UID}:${USER_GID}

ENTRYPOINT ["/telemetrygen"]
