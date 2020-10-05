# Layout is based on
# https://github.com/glencoesoftware/omero-ms-thumbnail/blob/v0.5.2/Dockerfile
ARG IMAGE=adoptopenjdk/openjdk11:jre-11.0.7_10-alpine
FROM ${IMAGE}

WORKDIR /opt/ms

ARG NAME=omero-ms-image-region-0.5.3-SNAPSHOT-7
RUN wget -q https://ci.appveyor.com/api/buildjobs/dk9f2th3rto31yt2/artifacts/build%2Fdistributions%2F${NAME}.zip \
        -O ${NAME}.zip && \
    unzip -q ${NAME} && \
    mv ${NAME}/* . && \
    rm -r ${NAME}.zip ${NAME}

EXPOSE 8080
ENV JAVA_OPTS "-Xmx1G"

ENTRYPOINT ["sh", "/opt/ms/bin/omero-ms-image-region"]
