# docker-remotely

[![Build Docker Images](https://github.com/Allram/docker-remotely/actions/workflows/main.yml/badge.svg)](https://github.com/Allram/docker-remotely/actions/workflows/main.yml) [![Get latest release version](https://github.com/Allram/docker-remotely/actions/workflows/GetVersion.yml/badge.svg)](https://github.com/Allram/docker-remotely/actions/workflows/GetVersion.yml)

Automated builds through github actions, will run at 10.00 when a new release is found.

## Usage

Docker:
```
docker run --rm --name remotely -v /appdata/remotely:/config -p 5000:5000 allram/remotely:latest
```

Docker-Compose
```
version: "2"
services:
  remotely:
    image: allram/remotely:latest
    ports:
      - 5000:5000
    volumes:
      - /appdata/remotely:/config

```
