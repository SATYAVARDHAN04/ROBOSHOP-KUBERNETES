# IMPLEMENTING ROBOSHOP PROJECT USING KUBERNETES

**SOME IMPORTANT POINTS AND COMMANDS TO NOTE** 0. Create a seperate namespace named "roboshop" for this entire project deployment

1. For every microservice it is better to create deployment,service.
2. Instead of running kubectl apply -f <filename> for every microservice we use an alias name as

```bash
alias ka="kubectl apply -f manifest.yaml"
```

3. Instead of running kubectl get pods for every microservice we use an alias name as

```bash
alias kp="kubectl get pods"
```

_NOTE: Since we are creating the project in the "roboshop" namespace we need to mention the namespace while running the commands._

```bash
kp -n roboshop
```
