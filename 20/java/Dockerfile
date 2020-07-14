FROM philipssoftware/openjdk:11

MAINTAINER Forest Keepers

ARG wss_latest_release_version=20.6.2
ENV WSS_LATEST_RELEASE_VERSION $wss_latest_release_version

USER root

RUN apt-get update && apt-get install -y \
  unzip

RUN mkdir -p /app
RUN cd /app

WORKDIR /app

RUN curl -o /app/wss-unified-agent.jar https://unified-agent.s3.amazonaws.com/wss-unified-agent-$WSS_LATEST_RELEASE_VERSION.jar 

RUN java -jar wss-unified-agent.jar -v

ADD REPO .
ADD TAGS .

CMD java -jar wss-unified-agent.jar
