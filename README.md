# CKA Labs – Certified Kubernetes Administrator

This repository documents my **hands-on preparation for the Certified Kubernetes Administrator (CKA)** exam.

All labs are performed on a **self-built multi-node Kubernetes cluster** using **kubeadm** on **VMware**, following real-world administrative and troubleshooting scenarios.

This repository is designed to:
- Align strictly with the **CKA exam blueprint**
- Demonstrate **practical Kubernetes administration skills**
- Serve as a **foundation for CKS and OSCP-level security work**

---

## 🧠 Skills Demonstrated

- Kubernetes cluster setup and administration
- Workload scheduling and lifecycle management
- Service networking and DNS troubleshooting
- Persistent storage configuration
- Configuration management (ConfigMaps & Secrets)
- Observability (logs, metrics, probes)
- Cluster and application troubleshooting
- Kubernetes security fundamentals (RBAC, SecurityContext)

---

## 🏗️ Lab Environment

- **Virtualization**: VMware
- **Cluster Type**: kubeadm-based
- **Nodes**:
  - 1 Control Plane
  - 2 Worker Nodes
- **OS**: Linux
- **Container Runtime**: containerd
- **CNI**: (documented in environment setup)
- **kubectl**: CLI-driven (exam-style)

---

## 📂 Repository Structure

Each folder maps directly to **CKA exam domains**:
- 00-environment-setup/ → Cluster & lab design
- 01-core-concepts/ → Pods, namespaces, labels
- 02-workloads-scheduling/ → Deployments, jobs, affinity
- 03-services-networking/ → Services, DNS, ingress
- 04-storage/ → PV, PVC, StatefulSets
- 05-configuration/ → ConfigMaps, Secrets
- 06-observability/ → Logs, probes, monitoring
- 07-troubleshooting/ → Exam-style failure scenarios
- 08-security-basics/ → RBAC, ServiceAccounts

---

## 🧪 Lab Format

Each lab includes:
- YAML manifests
- CLI commands used
- Expected output
- Common mistakes & fixes
- Exam-focused tips

---

## 🎯 Certification Roadmap

- ✅ CKA (this repository)
- 🔜 CKS (security hardening & runtime defense)
- 🔜 OSCP (offensive + defensive container security)

---

## ⚠️ Note

This repository is **not copied from tutorials**.
All configurations, failures, and fixes are tested manually.

---
