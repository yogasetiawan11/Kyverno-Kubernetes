# Using Helm
Add helm repo for kyverno
```sh
helm repo add kyverno https://kyverno.github.io/kyverno/
helm repo update
```

Install kyverno in HA mode
```sh
 helm install kyverno kyverno/kyverno -n kyverno --create-namespace --set replicaCount=3

 # you can modify the replica count
```

Install a specific version of kyverno
```sh
helm search repo kyverno -l | head -n 10
```

## Example
```sh
helm install kyverno kyverno/kyverno -n kyverno --create-namespace --version 2.6.5
```

# Using Kubernetes manifest yaml files
```sh
kubectl create -f https://github.com/kyverno/kyverno/releases/download/v1.8.5/install.yaml
```