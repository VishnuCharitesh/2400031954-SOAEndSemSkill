# springboot-docker-demo

A minimal REST API built with Java 17, Spring Boot, and Maven.

## Files

- `pom.xml` declares the Java version, Spring Boot version, and Spring Web dependency.
- `src/main/java/com/example/demo/DemoApplication.java` starts the Spring Boot application.
- `src/main/java/com/example/demo/controller/HelloController.java` defines the three REST endpoints.
- `src/main/resources/application.properties` sets the server port to `8080`.
- `Dockerfile` builds the application in a Java 17 container and runs it in a smaller Java 17 runtime container.

## Build

From this directory, run:

```shell
mvn clean package
```

The executable JAR is created at `target/springboot-docker-demo-0.0.1-SNAPSHOT.jar`.

## Run locally

Start the application with:

```shell
mvn spring-boot:run
```

The application listens on port `8080`. Stop it with `Ctrl+C`.

## Test the endpoints

In another terminal, run:

```shell
curl http://localhost:8080/api/hello
curl http://localhost:8080/api/greet/Alex
curl http://localhost:8080/api/status
```

The greeting endpoint returns a greeting containing the name in the URL.

## Run with Docker

Build and start the container from this directory:

```shell
docker build -t springboot-docker-demo .
docker run --rm -p 8080:8080 springboot-docker-demo
```

Then use the same curl commands above. The `-p 8080:8080` option makes the container's port available on the host.
