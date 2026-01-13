# VMware Setup

## 🖥️ Virtual Machines

Each node is provisioned with:

- **vCPU**: 2
- **Memory**: 6 GB
- **Disk**: 25 GB
- **OS**: Linux (minimal install)

---

## 🔧 VMware Configuration

- **Networking Mode**: Bridged Adapter
- **Reason**:
  - Direct LAN access
  - Simplifies node-to-node communication
  - Closely mimics bare-metal behavior

---

## ⚠️ Considerations

- Host firewall rules must allow inter-node traffic
- IP conflicts avoided via DHCP reservations
- Snapshots avoided during active cluster operations
