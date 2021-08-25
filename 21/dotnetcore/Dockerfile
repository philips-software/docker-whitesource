FROM mcr.microsoft.com/dotnet/core/sdk:3.0.101

MAINTAINER Forest Keepers

ARG wss_latest_release_version=21.6.3
ENV WSS_LATEST_RELEASE_VERSION $wss_latest_release_version

RUN apt-get update \ 
    && apt-get -y install default-jre \
    && apt-get -q autoremove \
    && apt-get -q clean -y \
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/*.bin

WORKDIR /app

RUN curl -o wss-unified-agent.jar https://unified-agent.s3.amazonaws.com/wss-unified-agent-$WSS_LATEST_RELEASE_VERSION.jar

RUN java -jar wss-unified-agent.jar -v

COPY REPO .
COPY TAGS .

CMD java -jar wss-unified-agent.jar
