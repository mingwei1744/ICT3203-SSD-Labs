# ICT3203-SSD-Labs
ICT3203 Secure Software Development Labs

# Docker Containers
This branch contains the docker containers configurations for Jenkins

1. jenkins
- Standalone jenkins with DinD
2. jenkins-nginx
- Jenkins resided behind a reverse proxy

# jenkins-nginx
1. Create a ssl folder in the same directory as /jenkins-nginx
2. Generate your self-signed cert and place them in this directory

# Start Container
Build Image
```
docker build -t jenkins-blueocean:2.414.3-1 .
```
Start Container
```
docker-compose up -d
```

Note: Set up is done on Windows Environment. 
