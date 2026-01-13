# Pod Examples – CKA Core Concepts

This document contains common **Pod-related scenarios** frequently encountered in the **CKA exam**.

---

## 1️⃣ Single-Container Pod

### Create a basic nginx pod
```bash
kubectl run nginx --image=nginx --restart=Never

## Verify
kubectl get <resource>
kubectl describe <resource>

## Debug
kubectl logs <resource>
kubectl get events

## Cleanup
kubectl delete <resource>

