# Layout is based on
# https://github.com/glencoesoftware/omero-ms-thumbnail/blob/v0.5.2/Dockerfile
ARG IMAGE=adoptopenjdk/openjdk11:jre-11.0.7_10-alpine
ARG GRADLE_IMAGE=gradle:6.6.1-jdk8

#
# Build: Use the gradle image for building.
#
FROM ${GRADLE_IMAGE} as gradle
ARG OMERO_MS_IMAGE_REGION_VERSION=0.5.2

WORKDIR /home/gradle/omero-ms-image-region
RUN curl -sfL https://github.com/glencoesoftware/omero-ms-image-region/archive/v${OMERO_MS_IMAGE_REGION_VERSION}.tar.gz | \
    tar -zx --strip-components=1
RUN gradle build

WORKDIR /opt/ms
RUN ls /home/gradle/omero-ms-image-region/
RUN ls /home/gradle/omero-ms-image-region/build/
RUN tar xf /home/gradle/omero-ms-image-region/build/distributions/omero-ms-image-region-${OMERO_MS_IMAGE_REGION_VERSION}.tar --strip-components=1

#
# Install: Copy the built distribution into a clean container to minimize size.
#
FROM ${IMAGE}
COPY --from=gradle /opt/ms /opt/ms

EXPOSE 8080
ENV JAVA_OPTS "-Xmx1G"
WORKDIR /opt/ms

ENTRYPOINT ["sh", "/opt/ms/bin/omero-ms-image-region"]
