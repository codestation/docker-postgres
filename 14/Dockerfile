FROM postgres:14-bullseye

LABEL maintainer="codestation <codestation404@gmail.com>"

ENV BACKREST_VERSION=2.37-1.pgdg110+1
ENV S6_OVERLAY_VERSION=3.1.0.1

# Install pgbackrest
RUN set -ex; \
	apt-get update; \
	apt-get install -y --no-install-recommends \
		ca-certificates \
		curl \
		pgbackrest=${BACKREST_VERSION} \
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
