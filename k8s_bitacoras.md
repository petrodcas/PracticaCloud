## Repaso de Docker
Comenzamos repasando un poco Docker y sus comandos utilizados.
Algunos comando pasar recordar...

$sudo docker images
$sudo docker ps
$sudo docker build -t nombreimagen:1.0 .
$sudo docker run nombreimagen:1.0
$sudo docker push userdockerhub/nombreimagen:1.0
$sudo docker rm id_container
$sudo docker rmi id_image
$sudo docker rm $(docker ps -a -q)
$sudo docker rmi $(docker images -q)


## Entramos en Kubernetes

Ejecutando un deploy
$kubectl apply -f deployment.yml

Ver los deployments
$kubctl get deployments
$kubectl get pods
$kubectl delete -f deployment.yml
Entrando al Pod por comandos
$kubectl exec -it nombrepod -- /bin/bash

Deployments 
Crear Pods y ReplicaSets de forma declarativa.

No queremos enlazar directamente con los pods. Ya que estos son mortales. Nosotros tendremos que acceder a un punto único que sea invariable, este es el concepto del servicio. El punto de entrada. Este sabrá cuantos pods tiene y podrá dirigir el tráfico a unos o a otros.

Para ver los servicios
$kubectl get service

Para ver a ingress

$kubectl get ingress

Habilitar la funcionalidad de Ingress en Minikube
$minikube addons enable ingress

Para conocer la IP del Pod:
Primero hacemos: $kubectl get pods para conocer el nombre

127.17.0.5

Despues: $kubectl exec -it nombre_pod -- /bin/sh

//////////////////////////////////////////

Hablando de kubernetes y servicios

¿Como acceder a los pods?

Podemos acceder usando el servicio NodePort:

NodePort: lo que hace es crear un puerto especifico que apunta al servicio. Lo malo q tenemos que apuntar con la IP publica de cada worker.

$kubectl get pods -o wide

kubectl log -n ingress-nginx ingresspod


```
# 🛠️ Projecto Jira clone
![A simple example  working](https://camo.githubusercontent.com/dbbdafee8881f9b68dbcb42231615c31778b1a856165d13b4f76a649765e2295/68747470733a2f2f692e6962622e636f2f6276465062776b2f53637265656e73686f742d323032302d30332d32342d4a6972612d436c6f6e652e706e67)
## 🕹️Tecnologías usadas 
![Tech](https://camo.githubusercontent.com/741e40fb6efc6f7bc0b8a40e7dfca65219b483cf23656d4313b2b3687e2f5e4e/68747470733a2f2f692e6962622e636f2f4456466a38504c2f746563682d69636f6e732e6a7067)        
<center>
<img src="https://i.imgur.com/F2LSD9f.png">
</center>


## ⛑️ Información  de uso
Esta aplicación es un fork de  **oldboyxx/jira_clone** pero preparada para kubernetes y Docker.
## 🥸 Requisitos
``````
# 🛠️ Projecto Jira clone
![A simple example  working](https://camo.githubusercontent.com/dbbdafee8881f9b68dbcb42231615c31778b1a856165d13b4f76a649765e2295/68747470733a2f2f692e6962622e636f2f6276465062776b2f53637265656e73686f742d323032302d30332d32342d4a6972612d436c6f6e652e706e67)
## 🕹️Tecnologías usadas 
![Tech](https://camo.githubusercontent.com/741e40fb6efc6f7bc0b8a40e7dfca65219b483cf23656d4313b2b3687e2f5e4e/68747470733a2f2f692e6962622e636f2f4456466a38504c2f746563682d69636f6e732e6a7067)        
<center>
<img src="https://i.imgur.com/F2LSD9f.png">
</center>


## ⛑️ Información  de uso
Esta aplicación es un fork de  **oldboyxx/jira_clone** pero preparada para kubernetes y Docker.
## 🥸 Requisitos

## 🐋 Docker

1.1 Creación de Dockerfile 

Lo primero que se llevó a cabo fue la implementación de los Dockerfile para las imágenes. 
Algunos comandos utilizados fueron los siguientes:
**$sudo docker images 
$sudo docker ps 
$sudo docker build -t nombreimagen:1.0 . 
$sudo docker run nombreimagen:1.0 
$sudo docker login
$sudo docker push userdockerhub/nombreimagen:1.0 
$sudo docker stop id_container
$sudo docker rm id_container 
$sudo docker rmi id_image 
$sudo docker rm $(docker ps -a -q) 
$sudo docker rmi $(docker images -q)**

## 🏸 Kubernetes

**2.1 Implementación de Ingress**

Se utiliza el modelo de Ingress proporcionado por la documentación de Kubernetes. 

**$kubectl logs -n nombre_namespace nombre_pod** 

**2.2 Creación del deploy para el servicio** 

Se declaran el despliegue los pods de las imágenes, en este caso 2 réplicas para el frontend y dos réplicas para el backend. 

**2.2.1 Creación de los servicios**

Frontend y Backend tendrá cada uno asociado su servicio que servirá para darle flujo de entrada y salida a la información.

No queremos enlazar directamente con los pods. Ya que estos son mortales. Nosotros tendremos que acceder a un punto único que sea invariable, este es el concepto del servicio. El punto de entrada. Este sabrá cuantos pods tiene y podrá dirigir el tráfico a unos o a otros.

**2.2.3 Conexión con Ingress**

Esta conexión servirá para direccionar el tráfico desde el Load Balancer a cada uno los servicios.

**Comandos útiles para Kubernetes:**

$kubectl apply -f deployment.yml
$kubctl get deployments
$kubectl get services 
$kubectl get pods
$kubectl get pods -o wide 
$kubectl delete -f deployment.yml
$kubectl exec -it nombrepod -- /bin/bash

## 🧩 Secuencia de despliegue

1. Despliegue de Ingress para obtener la IP del Load Balancer.
2. Reemplazar en el código del frontend la referencia de la IP del backend por la obtenida del Load Balancer.
3. Generar las imágenes y subirlas al registro correspondiente.
4. Deplegar el deployment.yml 


















