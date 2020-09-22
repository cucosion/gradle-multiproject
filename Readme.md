Install tooling for testing

https://hub.docker.com/r/bitnami/sonarqube/tags
https://github.com/bitnami/bitnami-docker-sonarqube/tree/8.4.2-debian-10-r18
https://github.com/bitnami/bitnami-docker-sonarqube/blob/master/8/debian-10/Dockerfile

````
docker network create sonarqube-tier
docker volume create --name postgresql_data
docker run -d --name postgresql -e ALLOW_EMPTY_PASSWORD=yes -e POSTGRESQL_USERNAME=bn_sonarqube -e POSTGRESQL_DATABASE=bitnami_sonarqube -e POSTGRESQL_PASSWORD=bitnami1234 --net sonarqube-tier --volume postgresql_data:/bitnami/postgresql bitnami/postgresql:latest
docker volume create --name sonarqube_data
docker run -d --name sonarqube -p 8081:9000 -e ALLOW_EMPTY_PASSWORD=yes -e SONARQUBE_DATABASE_USER=bn_sonarqube -e SONARQUBE_DATABASE_NAME=bitnami_sonarqube -e SONARQUBE_DATABASE_PASSWORD=bitnami1234 --net sonarqube-tier --volume sonarqube_data:/bitnami bitnami/sonarqube:8.4.2
````

Use the link http://localhost:8081/ to access the ui and admin/bitnami to login. After login go an install necessary plugins as checkstyle and dependency check 
