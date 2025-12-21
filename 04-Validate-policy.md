# Mutate Policy
using this policy Every deployment should have simmilar labels (team: backend) 
```sh
apiVersion: kyverno.io/v1
kind: ClusterPolicy
metadata:
  name: require-deployment-team-label
spec:
  validationFailureAction: Enforce
  rules:
  - name: require-deployment-team-label
    match:
      any:
      - resources:
          kinds:
          - Deployment
    validate:
      message: "You must have label 'team' for all deployments"
      pattern:
        metadata:
          labels:
            team: "backend"
            # here is the label
```

# Example file in deployment
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp-deployment
  labels:
    app: webapp
    team: backend    # Here you add additional parameter
spec:
  replicas: 3
  selector:
    matchLabels:
      app: webapp
  template:
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - name: webapp-container
        image: nginx:latest
        ports:
        - containerPort: 80
```