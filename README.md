# Automated Nginx Deployment with Ansible

This project uses one Ansible control node to install Nginx, enable it at boot,
and deploy a custom home page to two Ubuntu servers. Each page displays the
server's inventory name so you can tell which node served it.

## Prerequisites

- Ansible installed on the control node
- Two Ubuntu nodes reachable over SSH with sudo access
- Both nodes listed in `/etc/ansible/hosts` for this lab

## Deploy

```bash
ansible-playbook -i /etc/ansible/hosts site.yml
```

## Verify

```bash
ansible all -i /etc/ansible/hosts -m command -a "curl -fsS http://localhost/index.html"
```

Both nodes returned the custom home page. An immediate second playbook run
reported `changed=0` and `failed=0` on both nodes.
