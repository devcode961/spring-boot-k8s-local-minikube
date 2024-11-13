Build the project using the following command:

```
mvn clean install -DskipTests
```

Run the project using the following command:

```
mvn spring-boot:run
```

# Docker

Build the docker image using the following command:

```
docker build -t <Your_DockerHub_Username>/spring-boot-crud:latest .
```

Run the docker image using the following command:

```
docker run -p 8080:8080 <Your_DockerHub_Username>/spring-boot-crud:latest
```

# DockerHub

Login to DockerHub using the following command:

```
docker login
```

Push the docker image to DockerHub using the following command:

```
docker push <Your_DockerHub_Username>/spring-boot-crud:latest
```

# Kubernetes running as miniKube on your local machine

Create secrets using the following command:

```
kubectl create secret generic db-secrets \
  --from-literal=DB_HOST=host.docker.internal \
  --from-literal=DB_PORT=5432 \
  --from-literal=DB_NAME=<database name> \
  --from-literal=DB_USER=<user_name> \
  --from-literal=DB_PASSWORD=<password>
```

Create a Kubernetes deployment using the following command:

```
kubectl apply -f k8s/deployment.yaml
```

Use host.docker.internal to connect to a service running on the host machine from a container.
This is useful for connecting to a database or other services running on the host machine from a container. For example,
if you have a database running on your host machine and you want to connect to it from a container, you can use
host.docker.internal as the host name in your connection string. This will allow the container to connect to the
database running on the host machine.

While creating kubernetes secrets,
you can use

```
host.docker.internal as the host name in your connection string 
```

to connect to a database running on the host machine from a container.

This will allow the container to connect to the database running on the host machine.
