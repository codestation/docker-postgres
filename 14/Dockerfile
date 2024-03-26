FROM postgres:14-bookworm

LABEL maintainer="codestation <codestation@megpoid.dev>"

ARG BACKREST_VERSION=2.50
ARG S6_OVERLAY_VERSION=3.1.5.0

# Install pgbackrest
RUN set -ex; \
	apt-get update; \
	DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
		ca-certificates \
		curl \
		pgbackrest=${BACKREST_VERSION}-* \
	; \
	rm -rf /var/lib/apt/lists/*;

RUN set -ex; \
		curl -L https://github.com/just-containers/s6-overlay/releases/download/v${S6_OVERLAY_VERSION}/s6-overlay-noarch.tar.xz -o /tmp/s6-overlay-noarch.tar.xz ; \
		tar -C / -Jxpf /tmp/s6-overlay-noarch.tar.xz ;\
		rm /tmp/s6-overlay-noarch.tar.xz ;\
		curl -L https://github.com/just-containers/s6-overlay/releases/download/v${S6_OVERLAY_VERSION}/s6-overlay-$(arch).tar.xz -o /tmp/s6-overlay-$(arch).tar.xz ; \
		tar -C / -Jxpf /tmp/s6-overlay-$(arch).tar.xz ;\
		rm /tmp/s6-overlay-$(arch).tar.xz

COPY services/ /etc/s6-overlay/s6-rc.d/

ENTRYPOINT ["/init"]
