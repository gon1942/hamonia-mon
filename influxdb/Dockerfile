FROM influxdb:latest
MAINTAINER Kevin Kim <chaeya@gmail.com>

USER root
# Time Zone Setting
RUN ln -snf /usr/share/zoneinfo/Asia/Seoul /etc/localtime && \
 echo "Asia/Seoul" > /etc/timezone

WORKDIR /app
COPY entrypoint.sh ./
RUN chmod u+x entrypoint.sh

ENTRYPOINT ["/app/entrypoint.sh"]
