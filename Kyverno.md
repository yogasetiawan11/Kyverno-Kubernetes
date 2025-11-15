# Kyverno
Kyverno is a Kubernetes-native policy engine designed specifically to manage, validate, mutate, and generate Kubernetes configurations.

Kyverno allows you to automate security, compliance, and best practices validation and deliver secure self-service to application teams.

kyverno is neccesary to managing according to the complance (Rules) of organization. every organization has particular rules. 

For example : There is a company A, this company has a comliance that, Nobody in organization who has access to create EC2 Instances with more than 32Gb ram. because oraganization has a concern billing issues 

As Devops engineer you have to make sure that compliance or rules are match. this process called as Governace

# Admission Controller
Not everybody has a knowledge of Golang language, Admission Controller basically does validate, mutate the authenticated and authorize users 
()[https://github.com/kyverno/policies]