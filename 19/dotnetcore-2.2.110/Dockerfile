FROM mcr.microsoft.com/dotnet/core/sdk:2.2

MAINTAINER Forest Keepers

ARG wss_latest_release_version=19.12.2
ENV WSS_LATEST_RELEASE_VERSION $wss_latest_release_version

RUN apt-get update \ 
    && apt-get -y install default-jre \
    && apt-get -q autoremove \
    && apt-get -q clean -y \
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/*.bin

# Install .NET 2.2.110 SDK
ENV DOTNET_SDK_VERSION_2_2_110 2.2.110

RUN curl -SL --output dotnet.tar.gz https://dotnetcli.blob.core.windows.net/dotnet/Sdk/$DOTNET_SDK_VERSION_2_2_110/dotnet-sdk-$DOTNET_SDK_VERSION_2_2_110-linux-x64.tar.gz \
    && dotnet_sha512='cd3bc601ccc45edf38cdcc254831b88539dd51f26bdafa2d74eebb09d20d19d745fe319a93c4290e3b74a7a5d8fe851773a748ef0f23f7997c76b26e74d0d94f' \
    && echo "$dotnet_sha512 dotnet.tar.gz" | sha512sum -c - \
    && mkdir -p /usr/share/dotnet \
    && tar -zxf dotnet.tar.gz -C /usr/share/dotnet \
    && rm dotnet.tar.gz 

RUN mkdir -p /app
RUN cd /app

WORKDIR /app

RUN curl -o /app/wss-unified-agent.jar https://unified-agent.s3.amazonaws.com/wss-unified-agent-$WSS_LATEST_RELEASE_VERSION.jar 

RUN ls

RUN java -jar wss-unified-agent.jar -v

ADD REPO .
ADD TAGS .

CMD java -jar wss-unified-agent.jar
