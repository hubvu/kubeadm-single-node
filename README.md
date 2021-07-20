
## Single Node Kubernetes Cluster

<p align="center">
  <img alt="Bash Logo " width="150" height="100" src="./assets/bash.svg">
  <img alt="Plus Sign Logo" width="50" height="100" src="./assets/plus.svg">
  <img alt="Kubernets Logo" width="150" height="100" src="./assets/kubernetes.svg">
</p>

<p align="center">
  <a href="https://github.com/hubvu/kubeadm-single-node/actions" alt="ShellCheck">
    <img src="https://github.com/hubvu/kubeadm-single-node/actions/workflows/shellcheck.yaml/badge.svg?branch=main">
  </a>
  <a href="https://github.com/hubvu/kubeadm-single-node/releases" alt="GitHub Release">
    <img src="https://img.shields.io/github/v/release/hubvu/kubeadm-single-node">
  </a>
  <a href="./LICENSE.md" alt="MIT License">
    <img src="https://img.shields.io/badge/license-MIT-green.svg">
  </a>
  <a href="https://github.com/hubvu/kubeadm-single-node/tree/main#supported-distributions" alt="Supported Distributions">
    <img src="https://img.shields.io/badge/platform-debian%20%7C%20centos-lightgrey.svg">
  </a>
  <a href="https://img.shields.io/github/repo-size/hubvu/kubeadm-single-node.svg" alt="Repository Size">
    <img src="https://img.shields.io/github/repo-size/hubvu/kubeadm-single-node.svg">
  </a>
  <a href="https://img.shields.io/github/directory-file-count/hubvu/kubeadm-single-node.svg" alt="Repository File Count">
    <img src="https://img.shields.io/github/directory-file-count/hubvu/kubeadm-single-node.svg">
  </a>
</p>

- [Single Node Kubernetes Cluster](#single-node-kubernetes-cluster)
  - [What is this?](#what-is-this)
  - [Resource Requirements](#resource-requirements)
  - [Dependencies](#dependencies)
  - [Supported Distributions](#supported-distributions)
  - [Quick-start & Usage](#quick-start--usage)
  - [Contributing](#contributing)
  - [Acknowledgements](#acknowledgements)
  - [License](#license)

### What is this?

* A collection of bash scripts that automates the installation of a Kubernetes cluster onto a single node.
* `kubeadm` is used to bootstrap the cluster and you are provided with an option to choose `docker` or `containerd` as your container runtime.
* Before creating the cluster, you will be asked to pick a container network interface. Below are the list of container network interfaces available in this project;
  * `calico` , `cilium` , `flannel` , `kube-router` , `weavenet`
* After bootstrapping and creating the Kubernetes cluster, there is an option to install useful tooling, such as;
  * `helm` , `kubernetes-dashboard` , `kubernetes-metrics-server` , `grafana` , `prometheus` , `weavescope` , `falco` , `gatekeeper` 
* For more information on how the bash scripts are organised, review the [Architecture](./ARCHITECTURE.md) document.

### Resource Requirements

* For minimum `kubeadm` resource requirements, refer to the [official `kubeadm` installation guide](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/).

### Dependencies

* Required utilities to ensure that the scripts execute successfully.
  * `bash` , `pwgen` , `tar` , `curl` , `bash-completion`, `epel-release`

### Supported Distributions

* Tested on;
  * `debian-10` , `centos-8-stream`

### Quick-start & Usage

```bash
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

### Contributing

* Contribution guidelines for this project can be found in the [Contributing](./CONTRIBUTING.md) document.

### Acknowledgements

* [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html).
* [ShellCheck](https://github.com/koalaman/shellcheck).
* [Shell Linter - GitHub Action](https://github.com/azohra/shell-linter).
* [SVG Logos](https://github.com/gilbarbara/logos).


### License

* Licenced under the [MIT License](./LICENSE.md).
