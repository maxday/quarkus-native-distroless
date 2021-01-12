# How to build a Distroless image for Quarkus ?

This is an hello-world app to showcase the Distroless image

## Running the application in dev mode


Step 1 : build the app in native mode 
```shell script
./mvnw package -Pnative -Dquarkus.native.container-runtime=docker  
```

## Dockerize the app using the provided Dockerfile

The application can be packaged using:
```shell script
docker build -f src/main/docker/Dockerfile.distroless -t maxday/quarkus-native-distroless .
```

## Run it !
```shell script
quarkus-native-distroless % docker run -it -p 8080:8080 maxday/quarkus-native-distroless:latest
```

The application is now runnable using `java -jar target/quarkus-native-distroless-1.0.0-runner.jar`.

## Size

You can create a native executable using: 
```shell script
docker images | grep maxday/quarkus-native-distroless                                                               
```
Outputs: 
```shell script
maxday/quarkus-native-distroless     latest     c245c7c9299f     5 minutes ago     59.6MB
```
