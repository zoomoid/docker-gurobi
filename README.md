# docker-gurobi

> **This project is deprecated due to a lack of willingness to maintain it. It was worth the try, I learned a lot in the process, but ultimately, I cannot afford a Gurobi licence that supports cgroup running, which is the limiting factor for this docker image. Use at your own risk!**

This repository contains a Dockerfile to create a Docker image for solving linear programming optimization problems with
Gurobi. The image itself is NOT hosted on Docker Hub!

NOTE that you have to have a floating license (i.e. a valid license server running and a connection to such) to run the image. Discovering this costed way too much time.

# Usage

```
docker run -e 'GUROBI_LICENSE=your-license-key' -v /path/to/license:/home/gurobi -v /path/to/scripts:/usr/src/gurobi/scripts --network 'host' docker-gurobi
```

# With docker-compose

```
version: '3'

services:
  gurobi:
    build: <path to Dockerfile>
    image: docker-gurobi:latest
    container_name: gurobi811
    environment:
      - 'GUROBI_LICENSE=your-license-key'
      - 'VERBOSE=<DEBUG MODE?yes:no>'
    volumes:
      - /path/to/license:/home/gurobi
      - /path/to/scripts:/usr/src/gurobi/scripts
    network_mode: "host"
```
