# 

```yaml
apiVersion: kyverno.io/v1
kind: ClusterPolicy
metadata:
  name: Deny-public-registry
spec:
  validationFailureAction: Enforce
  rules:
  - name: Deny-public-registries
    match:
      any:
      - resources:
          kinds:
          - Pod
    validate:
      message: "Use Image only from yogas4 registry"
      pattern:
        metadata:
          spec:
            containers:
              - image: "yogas4/*"
                # This ensure pods creation should create  from "yogas4" registry            