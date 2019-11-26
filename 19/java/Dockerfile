FROM philipssoftware/openjdk:11

MAINTAINER Forest Keepers

RUN mkdir -p /app
RUN cd /app

RUN curl -o /app/wss-unified-agent-19.10.1.jar https://unified-agent.s3.amazonaws.com/wss-unified-agent-19.10.1.jar 
RUN apt-get update && apt-get install -y \
    gradle

CMD java -jar wss-unified-agent-19.10.1.jar
