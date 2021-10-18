FROM philipssoftware/node:lts-java

MAINTAINER Forest Keepers

ARG wss_latest_release_version=21.9.1
ENV WSS_LATEST_RELEASE_VERSION $wss_latest_release_version

USER root

RUN apt-get update && apt-get install -y \
  unzip

WORKDIR /app

RUN curl -o wss-unified-agent.jar https://unified-agent.s3.amazonaws.com/wss-unified-agent-$WSS_LATEST_RELEASE_VERSION.jar

RUN java -jar wss-unified-agent.jar -v

COPY REPO .
COPY TAGS .

CMD java -jar wss-unified-agent.jar
