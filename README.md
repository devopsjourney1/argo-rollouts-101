# argo-rollouts-101

## Install ArgoRollouts into your Cluster
https://argoproj.github.io/argo-rollouts/installation/#controller-installation
```
kubectl create namespace argo-rollouts
kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml
```

## Install argo rollouts plugin for kubectl
https://argoproj.github.io/argo-rollouts/installation/#kubectl-plugin-installation
```
brew install argoproj/tap/kubectl-argo-rollouts
```

## Rollout Demo

1. Create the rollout and service
```
kubectl apply -f https://raw.githubusercontent.com/argoproj/argo-rollouts/master/docs/getting-started/basic/rollout.yaml
kubectl apply -f https://raw.githubusercontent.com/argoproj/argo-rollouts/master/docs/getting-started/basic/service.yaml
```

2. Watching rollouts

Via CLI:
```
kubectl argo rollouts get rollout rollouts-demo --watch
```

Dashboard:
```
kubectl argo rollouts dashboard
```

3. Rollout a new image

Change the image of the docker image you are using. Experiment with `blue`, `yellow`, `green`, `red`, etc.  
```
kubectl argo rollouts set image rollouts-demo \
  rollouts-demo=argoproj/rollouts-demo:yellow
```

Once you set the image, use the methods in step 2 to watch the rollout. If you want to connect to the application the below command works in minikube - otherwise you need to setup an ingress.

```
minikube service --all -n default
```




# Reference
https://argoproj.github.io/argo-rollouts/getting-started/
