FROM mcr.microsoft.com/dotnet/core/sdk:3.0.101

MAINTAINER Forest Keepers

ARG wss_latest_release_version=19.12.2
ENV WSS_LATEST_RELEASE_VERSION $wss_latest_release_version

RUN apt-get update \ 
    && apt-get -y install default-jre \
    && apt-get -q autoremove \
    && apt-get -q clean -y \
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/*.bin

RUN mkdir -p /app
RUN cd /app

WORKDIR /app

RUN curl -o /app/wss-unified-agent.jar https://unified-agent.s3.amazonaws.com/wss-unified-agent-$WSS_LATEST_RELEASE_VERSION.jar 

RUN ls

RUN java -jar wss-unified-agent.jar -v

ADD REPO .
ADD TAGS .

CMD java -jar wss-unified-agent.jar
