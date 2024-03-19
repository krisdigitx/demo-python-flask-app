![Deploy to AKS Cluster](https://github.com/kasunsjc/python-flask-docker/workflows/Deploy%20to%20AKS%20Cluster/badge.svg)
![Flask Application](https://github.com/kasunsjc/python-flask-docker/workflows/Flask%20Application/badge.svg)


# python-flask-docker
Basic Python Flask app in Docker which prints the hostname and IP of the container

### Build application
Build the Docker image manually by cloning the Git repo.
```
$ git clone https://github.com/lvthillo/python-flask-docker.git
$ docker build -t lvthillo/python-flask-docker .
```

### Download precreated image
You can also just download the existing image from [DockerHub](https://hub.docker.com/r/lvthillo/python-flask-docker/).
```
docker pull lvthillo/python-flask-docker
```

### Run the container
Create a container from the image.
```
$ docker run --name my-container -d -p 8080:8080 lvthillo/python-flask-docker
```

Now visit http://localhost:8080
```
 The hostname of the container is 6095273a4e9b and its IP is 172.17.0.2. 
```

### Verify the running container
Verify by checking the container ip and hostname (ID):
```
$ docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' my-container
172.17.0.2
$ docker inspect -f '{{ .Config.Hostname }}' my-container
6095273a4e9b
```


### Install ArgoCD on AKS
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl get all -n argocd
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

# Attach ACR to AKS using using acr-name
```
az aks update -n demo-devApp-aks -g demo-devApp-mongoose-dev-rg --attach-acr ddademodevAppmongooseacr
```

OR

# Attach using acr-resource-id
```
az aks update -n myAKSCluster -g myResourceGroup --attach-acr <acr-resource-id>
```





