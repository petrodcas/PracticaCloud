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
