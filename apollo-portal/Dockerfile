# Dockerfile for apollo-portal
# Build with:
# docker build -t apollo-portal .
# Run with:
# docker run -p 9090:8080 -d --name apollo-portal apollo-portal

FROM java:8-jre
MAINTAINER Louis

ENV VERSION 0.7.0

RUN apt-get install unzip

ADD target/apollo-portal-${VERSION}-github.zip /apollo-portal/apollo-portal-${VERSION}-github.zip

RUN unzip /apollo-portal/apollo-portal-${VERSION}-github.zip -d /apollo-portal \
    && rm -rf /apollo-portal/apollo-portal-${VERSION}-github.zip \
    && sed -i '$d' /apollo-portal/scripts/startup.sh \
    && echo "tail -f /dev/null" >> /apollo-portal/scripts/startup.sh

EXPOSE 8080

CMD ["/apollo-portal/scripts/startup.sh"]
