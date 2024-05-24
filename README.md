- Pour utiliser un fichier YAML, il suffit de remplacer <nom-du-fichier.yaml> par le nom du fichier YAML.
- Dans mon cas, j'ai utilisé les fichiers rabbitmq.yaml, database/postgresql.yaml et backend/deployment.yaml.
- Mon namespace est minh.

- Créer un namespace :
  ```
  kubectl create namespace <nom-du-namespace> 
  ```

- Déployer RabbitMQ :
  ```
  kubectl create -f rabbitmq.yaml --namespace=<nom-du-namespace> 
  ```

- Déployer PostgreSQL :
  ```
  kubectl create -f database/postgresql.yaml --namespace=<nom-du-namespace>
  ```

- Déployer le serveur Node.js :
  ```
  kubectl create -f backend/deployment.yaml --namespace=<nom-du-namespace>
  ```

- Ajouter un autoscaler pour le serveur :
  ```
  kubectl autoscale deployment <nom-du-deploiement> --min=<nombre-minimum-de-replicas> --max=<nombre-maximum-de-replicas> --cpu-percent=<pourcentage-d-utilisation-de-CPU> --namespace=<nom-du-namespace> 
  ```

- Vérifier les ressources déployées :

```
kubectl get pods --namespace=<nom-du-namespace>
kubectl get services --namespace=<nom-du-namespace>
kubectl get deployments --namespace=<nom-du-namespace>
kubectl get namespace --namespace=<nom-du-namespace>
```

- Récupérer les logs d'un pod :
  `kubectl logs <nom-du-pod> --namespace=<nom-du-namespace>`

- Utiliser un fichier YAML pour créer, supprimer ou appliquer des ressources :

```
kubectl create -f <nom-du-fichier.yaml>
kubectl delete -f <nom-du-fichier.yaml>
kubectl apply -f <nom-du-fichier.yaml>
```
