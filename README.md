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

**4. We then configure mongodb deployment,service**

_NOTE: We configure the mongodb service as ClusterIP service type this is beacuse there will only be communication with the mongodb pod within the cluster and the mondodb pod will not be exposed out._

**5. We then configure catalogue deployment,service,configmap for storing the environment variables**

_NOTE: We configure the catalogue service as ClusterIP service type this is beacuse there will only be communication with the catalogue pod within the cluster and the catalogue pod will not be exposed out._

**6. Since we already hosted 2 microservices now we will test the connectivity of catalogue pod to the mongodb pod via mogodb service**

In order to do this follow the below steps
a. Create a test pod named debug
b. Write a docker file for the test pod which includes all the essential connectivity tools like telnet,ping etc
c. Check the connectivity of the catalogue service to mongodb service via telnet

**_NOTE:_**

_Q) Why can't we check this by taking the exec of the catalogue container???_

_A)We cant do this beacuse the docker image of catalogue is bare minimum containing only the necessary file and folder so without vioalting the best practises of docker by installing required packages to test the connectivity we create a new pod that is used only to test the connectivity of one pod to other.._
