# jenkins-docker
This file will setup Jenkins with a single command. Add the code below to a file called "docker-compose.yaml" and run the command

```bash
$ docker-compose up -d

# To Tear Down
$ docker-compose down
```

```yml
version: '3.7'
services: 
    jenkins: 
        image: jenkins/jenkins:lts
        container_name: "jenkins"
        labels: 
            kompose.service.type: nodeport
        ports: 
            - '9090:8080'
            - '444:8443'
            - '50000:50000'
        volumes: 
            - /srv/data/jenkins_data:/jenkins_home
            - /srv/data/jenkins:/var/jenkins_config

volumes: 
    jenkins_data:
        driver: local
    jenkins:
        driver: local
```