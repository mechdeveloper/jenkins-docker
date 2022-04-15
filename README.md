# Run Jenkins using Docker Desktop (linux containers)

## How to use
- clone this repository in your local machine where docker is running
  ```bash
  git clone https://github.com/mechdeveloper/jenkins-docker.git
  cd jenkins-docker
  ```
- To spin up services defined in docker-compose.yml file
  ```bash
  docker-compose up
  ```
- Browse to http://localhost:8080 and wait untill the Unlock Jenkins page appears
- Proceed to the [Post-installation setup wizard](https://www.jenkins.io/doc/book/installing/#setup-wizard).
  - Note: Jenkins admin user password can be found at `/var/jenkins_home/secrets/initialAdminPassword`.
- To stop the services 
    ```bash
    docker-compose down
    ```

## Components defined in docker-compose.yml

1. networks
    - Create bridge network in docker named `jenkins`

2. volumes 
    - jenkins-docker-certs
    - jenkins-data

    volume `jenkins-docker-certs` share Docker client TLS certificates and volume `jenkins-data` is required to persist jenkins data.

3. services
    - jenkins-blueocean
      - Builds jenkins image using `jenkins/Dockerfile` and runs a container in Docker
    - jenkins-docker
      - runs docker:dind Docker image In order to execute Docker commands inside Jenkins nodes

## Reference
- <https://www.jenkins.io/doc/book/installing/docker/>
