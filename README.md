# Kubernetes Cluster Automation with Ansible

🚀 Automated Kubernetes cluster deployment on AWS EC2 instances using Ansible playbooks.

## Features

- **Automated Setup**: Complete Docker, containerd, and Kubernetes installation
- **Master Node**: Automated cluster initialization with kubeadm
- **Worker Nodes**: Automatic joining to the cluster
- **CNI Network**: Flannel network plugin configuration
- **AWS Ready**: Optimized for Ubuntu EC2 instances

## Quick Start

1. **Setup your inventory**:
   ```bash
   # Edit inventory.ini with your EC2 instance details
   cp inventory.ini.example inventory.ini
   ```

2. **Add your SSH key**:
   ```bash
   # Place your AWS key pair in the directory
   cp your-key.pem aws-ec2.pem
   chmod 400 aws-ec2.pem
   ```

3. **Run the automation**:
   ```bash
   # Deploy complete cluster
   ansible-playbook -i inventory.ini main.yaml
   
   # Or run individual components
   ansible-playbook -i inventory.ini setup-ec2.yaml
   ansible-playbook -i inventory.ini k8s-master-setup.yaml
   ansible-playbook -i inventory.ini add-worker-node.yaml
   ```

## Requirements

- Ansible 2.9+
- AWS EC2 instances (Ubuntu 20.04+)
- SSH access to all nodes
- Security groups allowing Kubernetes ports (6443, 10250, etc.)

## Included Playbooks

- `setup-ec2.yaml` - Docker & Kubernetes package installation
- `k8s-master-setup.yaml` - Master node initialization
- `add-worker-node.yaml` - Worker node joining
- `main.yaml` - Complete deployment workflow