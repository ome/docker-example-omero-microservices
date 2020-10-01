# Layout is based on
# https://github.com/glencoesoftware/omero-ms-thumbnail/blob/v0.5.2/Dockerfile
ARG IMAGE=adoptopenjdk/openjdk11:jre-11.0.7_10-alpine
FROM ${IMAGE}

WORKDIR /opt/ms

RUN wget -q https://ci.appveyor.com/api/buildjobs/t1rcl93loph2bcts/artifacts/build%2Fdistributions%2Fomero-ms-thumbnail-0.5.2.zip \
        -O omero-ms-thumbnail-0.5.2.zip && \
    unzip -q omero-ms-thumbnail-0.5.2.zip && \
    mv omero-ms-thumbnail-0.5.2/* . && \
    rm -r omero-ms-thumbnail-0.5.2.zip omero-ms-thumbnail-0.5.2

EXPOSE 8080
ENV JAVA_OPTS "-Xmx1G"

ENTRYPOINT ["sh", "/opt/ms/bin/omero-ms-thumbnail"]
