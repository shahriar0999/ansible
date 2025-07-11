# Ansible Variables - Simple Guide

## 🎯 Lesson 15: Ansible Variables

### 🧃What are variables?
Variables are **placeholders** to store values like names, paths, ports, etc.

### 🧒 Imagine this:
You want to say “Hello” to your friend:

Instead of:
```yaml
msg: "Hello, John"
```
Use:
```yaml
vars:
  friend_name: John

tasks:
  - debug:
      msg: "Hello, {{ friend_name }}"
```

---

## 🧺 Lesson 16: Variable Types

### 📦 1. **String**:
```yaml
name: "Shahriar"
```

### 🔢 2. **Number**:
```yaml
age: 25
```

### 🧾 3. **List**:
```yaml
fruits:
  - apple
  - banana
  - mango
```

### 📚 4. **Dictionary**:
```yaml
person:
  name: "Ali"
  age: 22
  city: "Dhaka"
```

Use like:
```yaml
{{ person.name }} → "Ali"
```

---

## 📝 Lesson 17: Registering Variables & Precedence

### 🔄 Register Variables
Store task output in a variable.

```yaml
- name: Check a file
  stat:
    path: /etc/passwd
  register: file_info
```

Access it:
```yaml
{{ file_info.stat.exists }}
```

### 🎚️ Variable Precedence (Highest wins)

1. Command-line `-e`
2. Task-level `vars`
3. Play-level `vars`
4. Inventory
5. Role defaults

---

## 📦 Lesson 18: Variable Scoping

- Task-level: visible only in that task.
- Play-level: visible to all tasks in the play.
- Role-level: visible only to that role.

---

## 🪄 Lesson 19: Magic Variables

Built-in variables Ansible gives you:

```yaml
{{ inventory_hostname }} → current host name
{{ ansible_facts }} → system facts
{{ hostvars }} → variables of another host
```

---

## 💡 Summary Table

| Type         | Example                        |
|--------------|--------------------------------|
| String       | `name: "John"`                |
| Number       | `age: 30`                     |
| List         | `colors: [red, green]`        |
| Dictionary   | `user: { name: "Ali", age: 25 }` |
| Register     | Store task result             |
| Magic Vars   | Built-in by Ansible           |
| Precedence   | Higher beats lower            |
| Scope        | Where variable is visible     |
