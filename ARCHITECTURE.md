## Architecture 
- [Architecture](#architecture)
  - [Overview](#overview)
    - [Tree Organisation](#tree-organisation)

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

* Below is a quick overview of how the directory is organised and brief file descriptions.

```yaml
.
├── container-network-interfaces
│   ├── install_calico                    # script to install calico > https://github.com/projectcalico/calico
│   ├── install_cilium                    # script to install cilium > https://github.com/cilium/cilium
│   ├── install_flannel                   # script to install flannel > https://github.com/flannel-io/flannel
│   ├── install_kube_router               # script to install kube-router > https://github.com/cloudnativelabs/kube-router
│   └── install_weavenet                  # script to install weave > https://github.com/weaveworks/weave
├── container-runtimes
│   ├── containerd
│   │   ├── 99-kubernetes-cri.conf        # sysctl parameters file for iptables to see bridged traffic
│   │   ├── containerd.conf               # load overlay and br_netfilter kernel modules 
│   │   ├── install_containerd            # script to install containerd
│   │   └── remove_containerd             # script to remove containerd
│   └── docker
│       ├── daemon.json                   # configure a cgroup and log driver
│       ├── install_docker                # script to install docker
│       └── remove_docker                 # script to remove docker
├── helm
│   ├── install_helm                      # script to install helm
│   └── remove_helm                       # script to remove helm
├── kubernetes
│   ├── install_kubernetes                # script to install core kubernetes tooling
│   ├── kubectl_configure                 # script to configure kubectl for usage
│   ├── kubernetes.list                   # kubernetes repository path
│   ├── kubernetes.repo                   # kubernetes repository configuration
│   ├── remove_kubernetes                 # script to remove kubernetes
│   └── schedule_pods                     # script to allow pods to be scheduled on a master node
├── observability
│   ├── install_grafana                   # script to install grafana > https://github.com/grafana/grafana
│   ├── install_kubernetes_dashboard      # script to install kubernetes dashboard > https://github.com/kubernetes/dashboard
│   ├── install_metrics                   # script to install metrics server > https://github.com/kubernetes-sigs/metrics-server
│   ├── install_prometheus                # script to install prometheus > https://github.com/prometheus/prometheus
│   └── install_weavescope                # script to install weavescope > https://github.com/weaveworks/scope
├── reset
│   └── reset_kubeadm                     # script to reset a kubernetes cluster using kubeadm
├── security
│   ├── install_falco                     # script to install falco security > https://github.com/falcosecurity/falco
│   └── install_opa_gatekeeper            # script to install gatekeeper > https://github.com/open-policy-agent/gatekeeper
├── main                                  # script to bootstrap and create a kubernetes cluster
├── optional                              # script to install optional tools
└── teardown                              # script to reset or remove kubernetes tools
```
