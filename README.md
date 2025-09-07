# IMPLEMENTING ROBOSHOP PROJECT USING KUBERNETES

**SOME IMPORTANT POINTS AND COMMANDS TO NOTE**

**0. Create a seperate namespace named "roboshop" for this entire project deployment**

**1. For every microservice it is better to create deployment,service.**

**2. Instead of running kubectl apply -f <filename> for every microservice we use an alias name as**

```bash
alias ka="kubectl apply -f manifest.yaml"
```

**3. Instead of running kubectl get pods for every microservice we use an alias name as**

```bash
alias kp="kubectl get pods"
```

_NOTE: Since we are creating the project in the "roboshop" namespace we need to mention the namespace while running the commands._

```bash
kp -n roboshop
```

To avoid such extra typing of commands it is recommened to download **kubens**.

**kubens** is a command line tool to switch between namespaces in kubernetes.

link: https://github.com/ahmetb/kubectx?tab=readme-ov-file#manual-installation-macos-and-linux

```bash
sudo git clone https://github.com/ahmetb/kubectx /opt/kubectx
sudo ln -s /opt/kubectx/kubectx /usr/local/bin/kubectx
sudo ln -s /opt/kubectx/kubens /usr/local/bin/kubens
```

For switching the namespace we can use this command

```bash
kubens roboshop
```

We the install k9s command line tool for better visibility of the kubernetes resources.

```bash
curl -sS https://webinstall.dev/k9s | bash
```
