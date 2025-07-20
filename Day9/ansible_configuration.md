# 🧾 Ansible Configuration File Setup – 4 Methods

> Ansible searches for its configuration file (`ansible.cfg`) in a specific order. Below are four ways to create and use it.

---

## ✅ 1. Global Config (`/etc/ansible/ansible.cfg`)

```bash
su -                         # Switch to root user
mkdir -p /etc/ansible        # Create Ansible directory if not exist
nano /etc/ansible/ansible.cfg
```

📌 Example config:
```ini
[defaults]
inventory = /etc/ansible/hosts
host_key_checking = False
```

Then:
```bash
exit                         # Return to normal user
ansible --version            # Confirm config file is detected
```

---

## ✅ 2. User-Level Config (`~/.ansible.cfg`)

```bash
cd ~                         # Go to home directory
touch .ansible.cfg           # Create config file
nano .ansible.cfg
```

📌 Add content:
```ini
[defaults]
inventory = ~/ansible_hosts
retry_files_enabled = False
```

Then check:
```bash
ansible --version
```

---

## ✅ 3. Project-Specific Config (`./ansible.cfg`)

```bash
mkdir my-ansible-project
cd my-ansible-project
touch ansible.cfg
nano ansible.cfg
```

📌 Sample content:
```ini
[defaults]
inventory = ./hosts
host_key_checking = False
```

Check:
```bash
ansible --version
```

---

## ✅ 4. Custom-Named Config (via `ANSIBLE_CONFIG` env var)

```bash
mkdir newdir
cd newdir
touch my_ansible_configuration_file.cfg
nano my_ansible_configuration_file.cfg
```

📌 Add content:
```ini
[defaults]
inventory = ./hosts
```

Then export:
```bash
export ANSIBLE_CONFIG=./my_ansible_configuration_file.cfg
ansible --version
```

🔁 Optional (for one command only):
```bash
ANSIBLE_CONFIG=./my_ansible_configuration_file.cfg ansible all -m ping
```

---

## 📌 Ansible Config File Precedence Order

1. `ANSIBLE_CONFIG` environment variable  
2. `./ansible.cfg` (current directory)  
3. `~/.ansible.cfg` (user home)  
4. `/etc/ansible/ansible.cfg` (system-wide)
