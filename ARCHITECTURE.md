## Architecture 
- [Architecture](#architecture)
  - [Overview](#overview)
    - [Tree Organisation](#tree-organisation)
  - [Diagram Overview](#diagram-overview)

### Overview

* There are three key bash scripts in this project that are named `main`, `optional` and `teardown` which users will mostly interact with.
  1. [`main`](./main) - this script will cover bootstrapping and creating a kubernetes cluster on a Debian or CentOS host. To successfully standup a usable cluster, a user will be prompted twice during the installation to choose a;
     1. [Container runtime](./container-runtimes/) and a,
     2. [Container network interface](./container-network-interfaces/).
     3. **Optional** - there is a third optional prompt which will ask a user if they are interested in installing useful tools right after the cluster set up. A user can either exit this script or continue to install more tools available (see below).
  2. [`optional`](./optional) - this script provides a user with the option to either install;
     1. [Helm](./helm/) - `helm` may already be installed if the user chose `cilium` as their container network interface when creating their cluster with the `main` script.
     2. [Observability Tools](./observability/).
     3. [Security Tools](./security/).
  3. [`teardown`](./teardown) - this script will provide a user with the option to;
     1. [Reset `kubeadm`](./reset/) or,
     2. Completely tear down the cluster and remove all of the key Kubernetes components installed on the host.

#### Tree Organisation

```yaml
.
├── container-network-interfaces
│   ├── install_calico                    #
│   ├── install_cilium                    #
│   ├── install_flannel                   #
│   ├── install_kube_router               #
│   └── install_weavenet                  #
├── container-runtimes
│   ├── containerd
│   │   ├── 99-kubernetes-cri.conf        #
│   │   ├── containerd.conf               #
│   │   ├── install_containerd            #
│   │   └── remove_containerd             #
│   └── docker
│       ├── daemon.json                   #
│       ├── install_docker                #
│       └── remove_docker                 #
├── helm
│   ├── install_helm                      #
│   └── remove_helm                       #
├── kubernetes
│   ├── install_kubernetes                #
│   ├── kubectl_configure                 #
│   ├── kubernetes.list                   #
│   ├── kubernetes.repo                   #
│   ├── remove_kubernetes                 #
│   └── schedule_pods                     #
├── observability
│   ├── install_grafana                   #
│   ├── install_kubernetes_dashboard      #
│   ├── install_metrics                   #
│   ├── install_prometheus                #
│   └── install_weavescope                #
├── reset
│   └── reset_kubeadm                     #
├── security
│   ├── install_falco                     #
│   └── install_opa_gatekeeper            #
├── main                                  #
├── optional                              #
└── teardown                              #
```
 

### Diagram Overview


* ...
