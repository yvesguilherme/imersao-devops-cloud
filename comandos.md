```bash
# Jamais colocar o K3D em produção! É apenas para testes locais...

$ k3d cluster create
$ kubectl get nodes
$ docker container ls

### ---

$ k3d cluster list
$ k3d cluster create meucluster --servers 3 --agents 3
$ kubectl get nodes
$ docker container ls

### ---

$ k3d cluster list
$ k3d cluster delete
$ k3d cluster list
$ docker container ls 
$ k3d cluster delete meucluster

### ---

$ k3d cluster create meucluster --servers 3 --agents 3 -p "30000:30000@loadbalancer"
$ docker container ls 
$ kubectl get nodes

### ---

$ cd 02-devops4devs-02
$ docker build -t yg/review-filmes:v1 -f src/Review-Filmes.Web/Dockerfile src
$ docker push yg/review-filmes:v1

### ---

$ kubectl api-resources
$ kubectl apply -f k8s/deployment-postgre.yaml
$ kubectl get pod
$ kubectl get deploy
$ kubectl get replicaset 
$ kubectl describe pod postgre-6688d5bd55-7d62g
$ kubectl describe deployment postgre

### ---

$ kubectl api-resources
$ kubectl apply -f k8s/deployment-postgre.yaml
$ kubectl get service
$ kubectl get all

### ---

$ kubectl port-forward service/postgre 5432:5432 # abrir o dbeaver e verificar a conexão
$ kubectl apply -f k8s/deployment-front.yaml
$ kubectl get all
$ kubectl describe po reviewfilmes-6688d5bd55-7d12g && watch 'kubectl get po'

### ---

$ kubectl rollout history deployment reviewfilmes
$ kubectl rollout undo deployment reviewfilmes
```