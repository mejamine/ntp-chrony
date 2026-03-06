# NTP Installation and Configuration

This repository includes a playbook that installs and configures the **NTP (Network Time Protocol)** service on supported Linux systems.

It ensures the legacy `ntp` package is installed, configured with custom NTP servers, enabled, and properly synchronized.

⚠️ The playbook automatically fails on operating systems where the legacy `ntp` service is no longer supported (for example modern Fedora, RHEL 8+, Debian 10+). In such cases, **chrony should be used instead.**

---

## Tasks:

- Detect if legacy `ntp` is supported on the target OS  
- Fail execution if `ntp` is not supported  
- Install `ntp` package  
- Configure NTP servers in `/etc/ntp.conf`  
- Enable and start `ntpd` service  
- Restart service when configuration changes  
- Verify synchronization using `ntpq -p`  

---

## Supported Operating Systems

This playbook supports only systems where the legacy `ntp` package is still available.

### Supported:
- Older Debian versions (< 10)
- Older RedHat / CentOS versions (< 8)
- Older Fedora versions (< 16)

### Not Supported (Playbook will fail):
- Debian ≥ 10  
- RHEL / CentOS ≥ 8  
- Fedora ≥ 16  

For modern systems, use **chrony** instead.

---

## Using in AAP

### General Config :

1. **Inventory:** create from file or manually  
2. **Credential:** SSH username/password + sudo  

No survey is required unless you want to override default NTP servers.

---

## Variables

### Playbook Variables (defined inside the playbook)

- `ntp_servers`  
  Default:
  ```yaml
  ntp_servers:
    - 0.pool.ntp.org
    - 1.pool.ntp.org