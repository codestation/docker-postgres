FROM postgres:14-bullseye

LABEL maintainer="codestation <codestation404@gmail.com>"

ENV BARMAN_VERSION=2.18-1.pgdg110+1

# Install barman-cloud
RUN set -xe; \
	apt-get update; \
	apt-get install -y --no-install-recommends \
		barman-cli-cloud=${BARMAN_VERSION} \
	; \
	rm -rf /var/lib/apt/lists/*;
