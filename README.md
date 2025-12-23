# Kyverno
Kyverno is a Kubernetes-native policy engine designed specifically to manage, validate, mutate, and generate Kubernetes configurations.

Kyverno allows you to automate security, compliance, and best practices validation and deliver secure self-service to application teams.

kyverno is neccesary to managing according to the complance (Rules) of organization. every organization has particular rules. 

For example : There is a company A, this company has a comliance that, Nobody in organization who has access to create EC2 Instances with more than 32Gb ram. because oraganization has a concern billing issues 

As Devops engineer you have to make sure that compliance or rules are match. this process called as Governace

# Admission Controller
Not everybody has a knowledge of Golang language, Admission Controller basically does validate, mutate the authenticated and authorize users 

So manually you can force the governance of Kubernetes cluster using kyverno (dynamic adimission controller) where you can simplify process, instead of writting admission controller. you will just write kyverno costume resources, package it into yaml file and kyverno will automatically create this ``admission controller`` with some webhooks configuration. 

# Kyverno can Do these things: 
- Generate -> For example, Create a default network policy whenever a namespace is created.
- Validate -> For example, Block users from using ``latest`` tag in the deployment or pod resources.
- Mutate -> For example, Attach pod security policy for a pod that is created without any pod security policy configuration.
- Verify Images -> For example, Verify if the Images used in the pod resources are properly signed and verified images.

(Labs to get hands on experience with kyverno)[https://kodekloud.com/public-playgrounds/kubernetes-kyverno-lab]
