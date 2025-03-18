# Kubeadm Cluster with Vagrant

A lightweight Kubernetes cluster setup using K3s, automated with Vagrant for local development and testing.

## Features

- Single-command cluster provisioning
- 1 Control Plane (Master) node + 2 Worker nodes
- Automatic DNS configuration
- Idempotent provisioning scripts
- Private network isolation (192.168.56.0/24)

## Prerequisites

- [Vagrant](https://www.vagrantup.com/) (>= 2.3.0)
- [VirtualBox](https://www.virtualbox.org/) (>= 6.1)
- 8GB+ RAM (4GB minimum)
- 20GB+ free disk space
- bash/zsh terminal

## Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/ziyad-tarek1/kubeadm-cluster-vagrant.git
   cd kubeadm-cluster-vagrant
   ```

2. **Review configuration** (optional)
   - Edit `Vagrantfile` for resource allocation


3. **Start the cluster**
   ```bash
   vagrant up
   ```

4. **Verify installation** (after provisioning completes)
   ```bash
   vagrant ssh controlplane
   kubectl get nodes
   ```

## Cluster Details

| Node Name     | IP Address      | Role    | CPU | Memory |
|---------------|-----------------|---------|-----|--------|
| controlplane  | 192.168.56.101  | Master  | 2   | 2GB    |
| node01        | 192.168.56.102  | Worker  | 2   | 1GB    |
| node02        | 192.168.56.103  | Worker  | 2   | 1GB    |



## Usage

### Accessing Nodes
```bash
# Connect to master node
vagrant ssh controlplane

# Connect to worker nodes
vagrant ssh node01
vagrant ssh node02
```

### Cluster Management
```bash
# Check cluster status
kubectl get nodes -o wide

# Deploy test application
kubectl create deployment nginx --image=nginx:alpine
kubectl expose deployment nginx --port=80

# View cluster info
kubectl cluster-info
```

### VM Management
```bash
# Stop cluster
vagrant halt

# Restart cluster
vagrant up

# Destroy cluster
vagrant destroy -f

# SSH to specific node
vagrant ssh node01
```

### 👨‍💻 License
This project is licensed under a custom license. Unauthorized use, distribution, or modification is prohibited. Refer to the LICENSE file for details.

---

### 💡 Contributors
    - Ziyad Tarek Saeed - Author and Maintainer.

Happy vagranting! 🚀
