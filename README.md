## Single Node Kubernetes Cluster

<p align="center">
  <img alt="Bash Logo " width="150" height="100" src="./assets/bash.svg">
  <img alt="Plus Sign Logo" width="50" height="100" src="./assets/plus.svg">
  <img alt="Kubernets Logo" width="150" height="100" src="./assets/kubernetes.svg">
</p>

### What is this?

* A collection of bash scripts that automates the installation of a Kubernetes cluster onto a single node.
* `kubeadm` is used to bootstrap the cluster and you are provided with an option to choose `docker` or `containerd` as your container runtime.
* Before creating the cluster, you will be asked to pick a container network interface. Below are the list of available container network interfaces available;
  * `calico`
  * `cilium` 
  * `flannel` 
  * `kube-router` 
  * `weavenet`
* After bootstrapping and creating the Kubernetes cluster, there is an option to install useful tooling, such as;
  * `helm` 
  * `kubernetes-dashboard` 
  * `kubernetes-metrics-server` 
  * `grafana` 
  * `prometheus` 
  * `weavescope`
  * `falco` 
  * `gatekeeper` 
* For more information on how the bash scripts are organised, please review the [Architecture](./ARCHITECTURE.md) document.

### Why?

* 

### Dependencies

* Some required utilities to ensure that the scripts execute successfully.
  * `bash`
  * `pwgen`
  * `tar`
  * `curl`
  * `bash-completion`

### Quickstart

```
# clone the repository
$ git clone git@github.com:hubvu/kubeadm-single-node.git

# navigate into the directory
$ cd kubeadm-single-node/

# make 'main', 'optional' and 'teardown' into executable files
$ chmod +x main optional teardown

# run 'main' to start the Kubernetes cluster deployment
$ sudo ./main

# run 'optional' to install useful tools
$ sudo ./optional

# run 'teardown' to destroy the Kubernetes cluster deployment
$ sudo ./teardown
```

### Resource Requirements

* 

### Supported Distributions

* `debian-10`
* `centos-8-stream`

### Contributing

* Contribution guidelines for this project can be found in [Contributing](./CONTRIBUTING.md) document.

### License

* Licenced under the [MIT License](./LICENSE.md).
