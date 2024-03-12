# kubernates-spring-security

# Description du fichier YAML

Ce fichier YAML décrit une ressource Kubernetes de type Deployment. Il déploie une application nommée "evalsecurrity", avec deux répliques, utilisant une image Docker "lamineoziljr/evalspringse:v2" pour le conteneur appelé "evalspringmysqlsec". 

## Contenu détaillé du fichier YAML

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
metadata: Les métadonnées associées à cette ressource, y compris le nom de déploiement.
##
spec: Les spécifications du déploiement, y compris le nombre de répliques et les sélecteurs pour identifier les pods.
##
template: Le modèle pour créer de nouveaux pods.
##
metadata: Les métadonnées associées au modèle, y compris les libellés.
##
spec: Les spécifications des conteneurs dans le pod.
##
containers: La liste des conteneurs dans le pod.
##
name: Le nom du conteneur.
##
image: L'image Docker utilisée pour le conteneur.
##
imagePullPolicy: La politique de tirage de l'image, qui est "IfNotPresent" ici.
##
ports: Les ports exposés par le conteneur.
##
containerPort: Le port du conteneur qui sera exposé.
##
