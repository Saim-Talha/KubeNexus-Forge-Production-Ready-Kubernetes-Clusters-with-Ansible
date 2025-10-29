# KubeNexus — Forge Production-Ready Kubernetes Clusters with Ansible

KubeNexus is an open-source automation framework designed to simplify and standardize the deployment of highly available Kubernetes clusters on AlmaLinux using Ansible. Whether you’re a DevOps engineer, systems administrator, or a learner experimenting with Kubernetes, KubeNexus eliminates the complexity of multi-master and multi-node setups with a single playbook execution.

This project automates every stage of Kubernetes installation — from setting up dependencies and configuring CRI-O as the container runtime to initializing the control plane, joining worker nodes, and deploying the Calico CNI for networking. Each component is modularized into Ansible roles, enabling flexibility, reusability, and easy customization for different environments.

KubeNexus ensures consistency across all nodes by enforcing system prerequisites, managing repositories dynamically, and validating cluster health post-deployment. It follows a role-based architecture, making it easy to extend for future enhancements like monitoring, storage integration, and load balancing.

---

## Key Features

- Automated installation of CRI-O, kubeadm, kubelet, and kubectl  
- Multi-master HA setup for production resilience  
- Seamless worker node joining mechanism  
- Calico CNI integration for pod networking  
- Modular Ansible role structure for scalability  
- Designed and tested on AlmaLinux (RHEL-compatible)  

---

## Project Structure

```
├── group_vars
│   └── all.yml
├── hosts.ini
├── roles
│   ├── crio
│   │   ├── handlers
│   │   │   └── main.yml
│   │   └── tasks
│   │       └── main.yaml
│   ├── kube
│   │   └── tasks
│   │       └── main.yml
│   ├── lb
│   │   └── tasks
│   │       └── main.yaml
│   ├── master_init
│   │   └── tasks
│   │       └── main.yml
│   ├── okd_ops
│   │   └── tasks
│   │       └── main.yml
│   ├── post_cluster_config
│   │   └── tasks
│   │       └── main.yaml
│   └── worker_join
│       └── tasks
│           └── main.yml
└── site-alma.yaml
```

---

## How It Works

1. **Prepare the Inventory:**  
   Add your master and worker nodes in `hosts.ini`.

2. **Set Cluster Variables:**  
   Modify configurations in `group_vars/all.yml` according to your environment.

3. **Run the Playbook:**  
   ```bash
   ansible-playbook -i hosts.ini site-alma.yml
   ```

4. **Wait for Completion:**  
   Once done, your fully functional multi-master Kubernetes cluster will be up and running.

---

## Role Breakdown

| Role | Description |
|------|--------------|
| **crio** | Installs and configures the CRI-O container runtime |
| **kube** | Installs Kubernetes components (kubeadm, kubelet, kubectl) 
| **master_init** | Initializes the first master node (control plane) |
| **worker_join** | Joins other masters and worker nodes to the cluster |
| **okd_ops** | Deploys OKD operators and supporting components |
| **post_cluster_config** | Applies final verifications and ensures cluster health |

---

## Tested Environment

**Operating System:** AlmaLinux 9  
**Ansible Version:**  
```bash
ansible [core 2.19.3]
python version = 3.11.14
jinja version = 3.1.6
pyyaml version = 6.0.3
```

---

## Why KubeNexus?

KubeNexus empowers engineers to focus on managing workloads, not infrastructure setup. By leveraging Ansible, it transforms complex Kubernetes deployments into a predictable, repeatable, and version-controlled process — making it ideal for both production and lab environments.

---

## Contribution

Contributions are welcome! Feel free to fork this repository, open issues, or submit pull requests to improve the automation and support additional distributions.



---

⭐ **If you find KubeNexus helpful, give it a star on GitHub!**
