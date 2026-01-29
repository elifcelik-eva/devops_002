## DevOps Projesi 002
### Gradle

---------------

## Docker 

### Image:
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
---
### Network :
###### Network'leri listeleme:
```
docker network ls
```
###### Network oluşturma:
```
docker network create -d bridge    my-network
```
###### Container'ı  network'e dahil etme:
```
docker network connect  my-network   my-app-1
docker network connect  my-network   my-app-2
docker network connect  my-network   my-app-3
```
###### Container network bağlantısını kesme:
```
docker network disconnect  my-network   my-app-1
docker network disconnect  my-network   my-app-2
docker network disconnect  my-network   my-app-3
```
###### Network silme:
```
docker network rm  my-network
```
---
### Volume: Container silinse bile data'yı tutan kalıcı storage
###### Volume listeleme:
```
docker volume ls
```
###### Volume oluşturma:
```
docker volume create my-volume
```
###### Volume detaylarını görme:
```
docker volume inspect my-volume
```
###### Container’a volume bağlama:
```
docker run -d --name my-app -v my-volume:/app/data   elifcelik49/devops_002:v001
``````
###### Container’a volume bağlama(Advanced):
```
docker run --mount source=my-volume,target=/app/data my-image
```
###### Volume silme:
```
docker volume rm my-volume
```
###### Kullanılmayan volume’ları temizleme:
```
docker volume prune
```
### Compose:
###### Compose oluşturma:
```
docker compose  -f  compose.yaml  up
```
###### Arka planda çalıştırma:
```
docker compose -f compose.yaml up -d
```
###### Çalışan servisleri listeleme:
```
docker compose ps
```
###### Logları izleme:
```
docker compose logs
```
###### Servisleri durdurma:
```
docker compose down
```
###### Volume’lar dahil silme:
```
docker compose down -v
```

## KUBERNETES (K8s)

### Minikube Kurulum:
```
https://minikube.sigs.k8s.io/
```
###### Windows:
```
winget install Kubernetes.minikube
```
###### Minikube çalıştırma:
```
minikube start
```
###### Minikube durdurma:
```
minikube stop
```
###### Minikube dashboard erişim:
```
minikube dashboard
```
### Kubernetes ile iletişim:
```
kubectl
```
###### Pod oluşturma:
```
kubectl  run  my-pod1  --image=elifcelik49/devops_002:v001  
```
###### Pod listesi:
```
kubectl get pods
kubectl get pod
kubectl get po
```
###### Pod detay:
```
kubectl get pods  -o wide
```
### Yaml dosyası ile pod oluşturma:
###### Pod oluşturma/güncelleme:
```
kubectl  apply  -f   _01_my_pod_create.yaml
```
######  Pod silme:
```
kubectl  delete  -f   _01_my_pod_create.yaml
```
###### Deployment oluşturma/güncelleme: ---> run komutu tek pod oluşturur; deployment ise replica sayısına göre birden fazla pod oluşturup yönetir.
```
kubectl  apply  -f   _01_my_deployment_create.yaml
```
######  Deployment silme:
```
kubectl  delete  -f   _01_my_deployment_create.yaml
```
###### Service oluşturma/güncelleme:  ---> Pod’ların IP’leri ve portları dinamik olduğundan, statik bir IP ve port aracılığıyla pod'lara sürekli network erişimi sağlar.
```
kubectl  apply  -f   _01_my_service_create.yaml
```
######  Service silme:
```
kubectl  delete  -f   _01_my_service_create.yaml
```
###  Port-Forward:
```
kubectl port-forward service/devops-002-1 9090:8080
```




