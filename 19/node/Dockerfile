FROM philipssoftware/node:10-java

MAINTAINER Forest Keepers

USER root

RUN apt-get update && apt-get install -y \
  unzip

RUN mkdir -p /app
RUN cd /app

RUN curl -o /app/wss-unified-agent-19.11.2.jar https://unified-agent.s3.amazonaws.com/wss-unified-agent-19.11.2.jar 

CMD java -jar wss-unified-agent-19.11.2.jar
