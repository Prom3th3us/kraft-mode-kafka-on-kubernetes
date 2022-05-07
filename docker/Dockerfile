FROM openjdk:11

ENV KAFKA_VERSION=3.0.1
ENV KAFKA_HOME=/opt/kafka
ENV PATH=${PATH}:${KAFKA_HOME}/bin


LABEL name="kafka" version=${KAFKA_VERSION}


RUN wget  https://downloads.apache.org/kafka/3.0.1/kafka-3.0.1-src.tgz 
RUN tar xfz kafka-3.0.1-src.tgz 
RUN rm kafka-3.0.1-src.tgz 
RUN cd kafka-3.0.1-src && ./gradlew jar -PscalaVersion=2.13.6 
RUN mv kafka-3.0.1-src $KAFKA_HOME

COPY ./entrypoint.sh /
RUN ["chmod", "+x", "/entrypoint.sh"]
ENTRYPOINT ["/entrypoint.sh"]

