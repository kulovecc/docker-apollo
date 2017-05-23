# Dockerfile for apollo-configservice
# Build with:
# docker build -t apollo-configservice .
# Run with:
# docker run -p 8080:8080 -d --name apollo-configservice apollo-configservice

FROM java:8-jre
MAINTAINER Louis

ENV VERSION 0.7.0

RUN apt-get install unzip

ADD target/apollo-configservice-${VERSION}-github.zip /apollo-configservice/apollo-configservice-${VERSION}-github.zip

RUN unzip /apollo-configservice/apollo-configservice-${VERSION}-github.zip -d /apollo-configservice \
    && rm -rf /apollo-configservice/apollo-configservice-${VERSION}-github.zip \
    && sed -i '$d' /apollo-configservice/scripts/startup.sh \
    && echo "tail -f /dev/null" >> /apollo-configservice/scripts/startup.sh

EXPOSE 8080

CMD ["/apollo-configservice/scripts/startup.sh"]
