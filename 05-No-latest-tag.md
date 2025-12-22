# Policy to Prevent use latest Image 
this policy will enforce a user when they create an image through deployment, the users should specify a tag and never use latest image in deployment.

## Kyverno Policy
```yaml 
# Policy to prevent using latest tag
apiVersion: kyverno.io/v1
kind: ClusterPolicy
metadata:
  name: no-latest-tag-policy
spec:
  validationFailureAction: Enforce
  rules:
  - name: require-image-tag
    match:
      any:
      - resources:
          kinds:
          - Deployment
    validate:
      message: "Must use an image tag"
      pattern:
        spec:
          containers:
          - image: "*:*"


  - name: don't allow latest tag
    match:
      any:
      - resources:
          kinds:
          - Pod
    validate:
      message: "don't use latest image"
      pattern:
        spec:
          containers:
          - image: "!*:latest"
          # It will ensure that it will no use the latest tag
```

## Example incorect Deployment 
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