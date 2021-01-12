# How to build a Distroless image for Quarkus ?

This is a hello-world app to showcase a Quarkus native app in a Distroless container


**Step 1** : build the app in native mode 
```shell script
./mvnw package -Pnative -Dquarkus.native.container-runtime=docker  
```

**Step 2** : Dockerize the app using the provided Dockerfile

The application can be packaged using:
```shell script
docker build -f src/main/docker/Dockerfile.distroless -t maxday/quarkus-native-distroless .
```

**Step 3** : run it ! 
```shell script
quarkus-native-distroless % docker run -it -p 8080:8080 maxday/quarkus-native-distroless:latest
```

The application is now runnable using `java -jar target/quarkus-native-distroless-1.0.0-runner.jar`.

**Image size**

```shell script
docker images | grep maxday/quarkus-native-distroless                                                               
```
Outputs: 
```shell script
maxday/quarkus-native-distroless     latest     c245c7c9299f     5 minutes ago     59.6MB
```
