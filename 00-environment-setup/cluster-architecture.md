# Kubernetes Cluster Architecture – High Availability Lab

This lab documents a **High Availability (HA) Kubernetes cluster** with 3 master nodes and 3 worker nodes, designed for **CKA, CKS practice, and real-world scenarios**.

---

## 🧩 Cluster Topology

| Node Role      | Hostname        | Purpose                                      | vCPU | Memory | Disk |
|----------------|----------------|---------------------------------------------|------|--------|------|
| Master Node    | k8s-master-1   | API Server, Scheduler, Controller Manager   | 2    | 6 GB   | 25 GB|
| Master Node    | k8s-master-2   | API Server, Scheduler, Controller Manager   | 2    | 6 GB   | 25 GB|
| Master Node    | k8s-master-3   | API Server, Scheduler, Controller Manager   | 2    | 6 GB   | 25 GB|
| Worker Node    | k8s-worker-1   | Application workloads                        | 2    | 6 GB   | 25 GB|
| Worker Node    | k8s-worker-2   | Application workloads                        | 2    | 6 GB   | 25 GB|
| Worker Node    | k8s-worker-3   | Application workloads                        | 2    | 6 GB   | 25 GB|

---

## 🔗 High Availability Design

1. **Control Plane HA**
   - 3 master nodes with **stacked etcd cluster**
   - Ensures **API server redundancy**
   - Load balancer required for API access (HAProxy or Nginx LB)
   
2. **Worker Nodes**
   - 3 nodes for application workloads
   - Supports **pod scheduling, draining, and failover testing**

3. **Networking**
   - Bridged adapter on VMware for all nodes
   - Each node has a **static IP**
   - Pod Network managed by CNI plugin (Calico/Flannel/Weave)

4. **Cluster Components**
   - kube-apiserver: HA via 3 masters + LB
   - etcd: 3-node cluster (master nodes)
   - kube-scheduler & kube-controller-manager: leader election enabled
   - kubelet & kube-proxy: on all nodes

---

## 🌐 IP Addressing (Example)

| Node           | Role           | IP Address       |
|----------------|----------------|----------------|
| k8s-master-1   | Master         | 192.168.8.201 |
| k8s-master-2   | Master         | 192.168.8.202 |
| k8s-master-3   | Master         | 192.168.8.203 |
| k8s-worker-1   | Worker         | 192.168.8.204 |
| k8s-worker-2   | Worker         | 192.168.8.205 |
| k8s-worker-3   | Worker         | 192.168.8.206 |
| LB             | HA Proxy       | 192.168.8.11 |

> 💡 Notes:
> - API requests go through the **load balancer** to any master node.
> - Pod and service networks are **overlay networks**, independent of host IPs.

---

## ⚙️ Design Decisions

- **3 Master Nodes**
  - Mimics production HA clusters
  - Supports **etc backups, failover, and leader election** practice
- **3 Worker Nodes**
  - Supports scaling, rolling updates, draining
  - Provides **realistic scheduling scenarios**
- **VM Specs**
  - 2 vCPU, 4GB RAM per node is enough for lab testing
- **VMware Networking**
  - Bridged mode ensures easy inter-node communication and external access

---

## 🔐 Security Considerations

- SSH keys for all nodes
- kubeconfig restricted per admin/role
- Firewall disabled for lab, but documented rules for production ready

---

## 🏗️ Optional Enhancements (CKS / OSCP Prep)

- Add **monitoring node** (Prometheus + Grafana)
- Enable **private CNI IP range** to simulate segmented networks
- Deploy **network policies** to test traffic filtering
- Test **etcd snapshot and restore** scenarios

![HA Kubernetes Cluster Diagram](../assets/diagrams/ha-cluster-3-master-3-worker.png)
