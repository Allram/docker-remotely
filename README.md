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

NGINX-Example
```
server {
    listen        80;
    server_name   example.com *.example.com;
    location / {
        proxy_pass         http://localhost:5000;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade $http_upgrade;
        proxy_set_header   Connection keep-alive;
        proxy_set_header   Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;
    }
    location /_blazor {    
        proxy_pass http://localhost:5000;    
        proxy_http_version 1.1;    
        proxy_set_header Upgrade $http_upgrade;    
        proxy_set_header Connection "upgrade";    
        proxy_set_header Host $host;    
        proxy_cache_bypass $http_upgrade;    
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;    
        proxy_set_header   X-Forwarded-Proto $scheme;    
    }    
    location /AgentHub {    
        proxy_pass http://localhost:5000;    
        proxy_http_version 1.1;    
        proxy_set_header Upgrade $http_upgrade;    
        proxy_set_header Connection "upgrade";    
        proxy_set_header Host $host;    
        proxy_cache_bypass $http_upgrade;    
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;    
        proxy_set_header   X-Forwarded-Proto $scheme;    
    }    
    location /ViewerHub {    
        proxy_pass http://localhost:5000;    
        proxy_http_version 1.1;    
        proxy_set_header Upgrade $http_upgrade;    
        proxy_set_header Connection "upgrade";    
        proxy_set_header Host $host;    
        proxy_cache_bypass $http_upgrade;    
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;    
        proxy_set_header   X-Forwarded-Proto $scheme;    
    }    
    location /CasterHub {    
        proxy_pass http://localhost:5000;    
        proxy_http_version 1.1;    
        proxy_set_header Upgrade $http_upgrade;    
        proxy_set_header Connection "upgrade";    
        proxy_set_header Host $host;    
        proxy_cache_bypass $http_upgrade;    
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;    
        proxy_set_header   X-Forwarded-Proto $scheme;    
    }
}
```
