FROM grafana/grafana:latest
MAINTAINER Kevin Kim <chaeya@gmail.com>

USER root

# Time Zone Setting
RUN ln -snf /usr/share/zoneinfo/Asia/Seoul /etc/localtime && \
 echo "Asia/Seoul" > /etc/timezone

RUN apt-get update && apt-get install -y curl gettext-base && rm -rf /var/lib/apt/lists/*

WORKDIR /etc/grafana
COPY datasources ./datasources

WORKDIR /app
COPY entrypoint.sh ./
RUN chmod u+x entrypoint.sh

ENTRYPOINT ["/app/entrypoint.sh"]
