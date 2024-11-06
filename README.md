# K8 Setup Token Exchange 

- ## Start Minkube

```
minikube start
```

- ## Start Minikube Tunnel

    - ##### How It Works
      - When we start `minikube tunnel`, it sets up a network route on your machine.
      - It assigns external IPs to LoadBalancer services, making them accessible on the IP address from your local network.
      - It requires root privileges because it modifies routing on your local machine.

```
minikube tunnel
```

- ## Build Docker image for service

```
eval $(minikube docker-env)
docker images
docker build -t node-demo:latest .
```

- ## Create a configuration in YAML and apply it 

```
kubectl apply -f node-demo-deployment.yaml
kubectl apply -f node-demo-service.yaml
kubectl apply -f node-demo-gateway.yaml
kubectl apply -f envoy-filter.yaml
```

- ## Logs

```
kubectl logs -f node-demo-fd57c5b75-8d8p4 

or 

kubectl logs -f node-demo-fd57c5b75-8d8p4 -c istio-proxy
```

- Docker 

```
eval $(minikube docker-env)
docker images
docker build -t node-demo:latest .
docker rmi <id?>
```

kubectl logs -f node-demo-fd57c5b75-8d8p4 -c istio-proxy -n default
kubectl logs -f node-demo-fd57c5b75-8d8p4 -c istio-proxy

- Log

```
kubectl logs -f node-token-exchange-7f488f6fc8-fhrsd

kubectl logs -f node-demo-fd57c5b75-8d8p4 -c istio-proxy -n default
```

- ## Useful Commands

```
kubectl get deployments
kubectl delete deployment <id>


kubectl get services
kubectl delete service <id>

kubectl get envoyfilter
kubectl delete envoyfilter <id>

kubectl get pods
kubectl delete pods <id>

```