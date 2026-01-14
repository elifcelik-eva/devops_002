## DevOps Projesi 002
### Gradle

---------------

### Docker Image

###### Projeyi, Docker image haline getirme:

###### Version 1
```
docker build --build-arg JAR_FILE=build/libs/devops_002-1.0.0.jar --tag elifcelik49/devops_002:v001 .
```
###### Container olarak çalıştırma:

```
docker run -it -d -p 32776:8080 --name my-second-app elifcelik49/devops_002:v001
```

###### DockerHub'a image yükleme:
```
docker push	 elifcelik49/devops_002:v001
```

###### DockerHub'dan image çekme:
```
docker pull elifcelik49/devops_002:v001
```