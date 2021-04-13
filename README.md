# OMERO.server and OMERO.web with micro-services (docker-compose)

[![Actions Status](https://github.com/ome/docker-example-omero-microservices/workflows/Build/badge.svg)](https://github.com/ome/docker-example-omero-microservices/actions)


This is an example of running OMERO.server, OMERO.web and microservices in Docker.
This is under development.

OMERO.server is listening on the standard OMERO ports `4063` and `4064`.
OMERO.web and microservices are accessible via a proxy running on port `10080` (http://localhost:10080/).

Log in as user `root` password `omero`.


## Run

First pull the latest major versions of the containers:

    docker-compose pull

Then start the containers:

    docker-compose up -d
    docker-compose logs -f


## Included microservices:
- [omero-ms-zarr](https://github.com/ome/omero-ms-zarr)
- [omero-ms-thumbnail](https://github.com/glencoesoftware/omero-ms-thumbnail)
- [omero-ms-image-region](https://github.com/glencoesoftware/omero-ms-image-region)
