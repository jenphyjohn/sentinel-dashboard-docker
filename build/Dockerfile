FROM registry.cn-beijing.aliyuncs.com/jenphyjohn/alpine-java
MAINTAINER JenphyJohn "zhuangzf1989@126.com"

# set environment
ENV BASE_DIR="/home/sentinel" \
    SERVER_PORT="8021" \
    DASHBOARD_SERVER="localhost:8021" \
    PROJECT_NAME="sentinel-dashboard" \
    JAVA_OPTS=""

ARG SENTINEL_DASHBOARD_VERSION=1.7.1

WORKDIR $BASE_DIR

ADD sentinel-dashboard-${SENTINEL_DASHBOARD_VERSION}.jar sentinel-dashboard-${SENTINEL_DASHBOARD_VERSION}.jar
ADD bin/docker-entrypoint.sh bin/docker-entrypoint.sh

# set startup log dir
RUN mkdir -p logs \
	&& cd logs \
	&& touch start.out \
	&& ln -sf /dev/stdout start.out \
	&& ln -sf /dev/stderr start.out
RUN chmod +x bin/docker-entrypoint.sh

EXPOSE 8021
ENTRYPOINT ["bin/docker-entrypoint.sh"]
