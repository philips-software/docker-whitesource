FROM philipssoftware/openjdk:11-zulu-docker

MAINTAINER Forest Keepers

USER root

RUN mkdir -p /app
RUN cd /app

RUN curl -o /app/wss-unified-agent-19.12.2.jar https://unified-agent.s3.amazonaws.com/wss-unified-agent-19.12.2.jar 

CMD java -jar wss-unified-agent-19.12.2.jar
