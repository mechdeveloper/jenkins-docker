# Downloading and running Jenkins in Docker

## How to use
- To spin up services defined in docker-compose.yml file

    ```bash
    docker-compose up
    ```
- Proceed to the [Post-installation setup wizard](https://www.jenkins.io/doc/book/installing/#setup-wizard).

- To stop the services 
    ```bash
    docker-compose down
    ```
    
## Components defined in docker-compose.yml

1. networks
    - Create bridge network in docker named jenkins
2. volumes 
    - jenkins-docker-certs
    - jenkins-data

    to share Docker client TLS certificates needed to connect to Docker daemon and persist the Jenkins data
3. services
    - jenkins-blueocean
      - runs jenkinsci/blueocean Docker image as a container in Docker
    - jenkins-docker
      - runs docker:dind Docker image In order to execute Docker commands inside Jenkins nodes
