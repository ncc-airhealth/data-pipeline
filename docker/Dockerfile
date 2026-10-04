# syntax=docker/dockerfile:1

FROM chrislusf/seaweedfs:4.48 AS seaweedfs
FROM ghcr.io/prefix-dev/pixi:0.81.0 AS pixi
FROM ghcr.io/astral-sh/uv:0.12.22 AS uv

FROM python:3.12.15-slim-bookworm

ARG TARGETPLATFORM
RUN if [ "$TARGETPLATFORM" != "linux/amd64" ]; then \
      echo 'Build with --platform linux/amd64.' >&2; exit 1; \
    fi

ENV UV_PYTHON_DOWNLOADS=never

COPY --from=seaweedfs /usr/bin/weed /usr/local/bin/weed
COPY --from=pixi /usr/local/bin/pixi /usr/local/bin/pixi
COPY --from=uv /uv /uvx /usr/local/bin/

WORKDIR /workspace

RUN test -s /etc/ssl/certs/ca-certificates.crt \
    && python -c "import platform, sys; assert platform.machine() == 'x86_64', platform.machine(); assert sys.version_info[:3] == (3, 12, 15), sys.version" \
    && weed version \
    && pixi --version \
    && uv --version

CMD ["bash"]
