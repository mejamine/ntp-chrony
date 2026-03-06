# Chrony Installation and Configuration

This repository includes a playbook that installs and configures **Chrony** for time synchronization on modern Linux systems.

Chrony is the recommended implementation of the **Network Time Protocol (NTP)** on newer distributions and replaces the legacy `ntp` service.

The playbook automatically checks if Chrony is supported on the target operating system and fails if it is not supported.

---

## Tasks:

- Detect if Chrony is supported on the target OS  
- Fail execution if Chrony is not supported  
- Install `chrony` package  
- Configure NTP servers in `/etc/chrony.conf`  
- Enable and start `chronyd` service  
- Restart service when configuration changes  
- Verify synchronization using `chronyc sources`  

---

## Supported Operating Systems

This playbook supports modern Linux distributions where Chrony is the default time synchronization service.

### Supported:
- Fedora ≥ 16  
- RHEL / CentOS ≥ 8  
- Debian ≥ 10  

### Not Supported (Playbook will fail):
- Older systems that require the legacy `ntp` service  

---

## Using in AAP

### General Config :

1. **Inventory:** create from file or manually  
2. **Credential:** SSH username/password + sudo  

No survey is required unless you want to override the default NTP servers.

---

## Variables

### Playbook Variables (defined inside the playbook)

```yaml
ntp_servers:
  - 0.pool.ntp.org
  - 1.pool.ntp.org