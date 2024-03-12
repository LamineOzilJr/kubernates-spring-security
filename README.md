# kubernates-spring-security

# Description du fichier de deploiement

Ce fichier YAML décrit une ressource Kubernetes de type Deployment. Il déploie une application nommée "evalsecurrity", avec deux répliques, utilisant une image Docker "lamineoziljr/evalspringse:v2" pour le conteneur appelé "evalspringmysqlsec". 

## Contenu du fichier de deploiement

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: evalsecurrity
spec:
  replicas: 2
  selector:
    matchLabels:
      app: evalsecurrity
  template:
    metadata:
      labels:
        app: evalsecurrity
    spec:
      containers:
        - name: evalspringmysqlsec
          image: lamineoziljr/evalspringse:v2
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 8087
```

Details : 
##
# apiVersion: 
La version de l'API Kubernetes utilisée pour définir cette ressource.
##
# kind:
Le type de ressource Kubernetes, qui est un "Deployment" dans ce cas.
##
# metadata: 
Les métadonnées associées à cette ressource, y compris le nom de déploiement.
##
# spec: 
Les spécifications du déploiement, y compris le nombre de répliques et les sélecteurs pour identifier les pods.
##
# template: 
Le modèle pour créer de nouveaux pods.
##
# metadata: 
Les métadonnées associées au modèle, y compris les libellés.
##
# spec: 
Les spécifications des conteneurs dans le pod.
##
# containers: 
La liste des conteneurs dans le pod.
##
# name: 
Le nom du conteneur.
##
# image: 
L'image Docker utilisée pour le conteneur.
##
# imagePullPolicy: 
La politique de tirage de l'image, qui est "IfNotPresent" ici.
##
# ports: 
Les ports exposés par le conteneur.
##
# containerPort: 
Le port du conteneur qui sera exposé.
##


# Description des services

Ce fichier YAML décrit un service Kubernetes de type NodePort. Il crée un service nommé "evalsecurrity-service" qui expose le port 8087 de l'application "evalsecurrity" sur le port 8088 du conteneur, accessible via un NodePort (30005).

## Contenu du fichier service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: evalsecurrity-service
spec:
  type: NodePort
  selector:
    app: evalsecurrity
  ports:
    - name: http
      port: 8087
      targetPort: 8088
      nodePort: 30005

```
Details :
##
# apiVersion: 
La version de l'API Kubernetes utilisée pour définir cette ressource.
##
# kind: 
Le type de ressource Kubernetes, qui est un "Service" dans ce cas.
##
# metadata: 
Les métadonnées associées à cette ressource, y compris le nom du service.
##
# spec: 
Les spécifications du service, y compris le type de service (NodePort) et les ports exposés.
##
# selector: 
Les labels utilisés pour sélectionner les pods auxquels ce service s'applique.
##
# ports: 
Les ports exposés par le service.
##
# name: 
Le nom du port exposé.
##
# port:
Le port du service.
##
# targetPort: 
Le port sur lequel le service redirige le trafic vers les pods.
##
# nodePort: 
Le port accessible sur chaque nœud de la grappe.
##
