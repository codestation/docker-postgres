FROM postgres:14-bullseye

LABEL maintainer="codestation <codestation404@gmail.com>"

ENV BARMAN_VERSION=2.18-1.pgdg110+1
ENV PGBACKREST_VERSION=2.37-1.pgdg110+1

# Install barman-cloud
RUN set -xe; \
	apt-get update; \
	apt-get install -y --no-install-recommends \
		barman-cli-cloud=${BARMAN_VERSION} \
		pgbackrest=${PGBACKREST_VERSION} \
	; \
	rm -rf /var/lib/apt/lists/*;
