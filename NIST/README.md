# 📘 What is NIST?

**NIST** stands for the **National Institute of Standards and Technology**, a U.S. government agency that creates **technology, cybersecurity, and compliance standards**. Its frameworks are used globally — especially in **cloud, information security, risk management, and compliance**.

---

## 🔑 Why Should a DevOps Engineer or SysAdmin Learn NIST?

Because NIST provides **clear guidelines** for:

* Securing servers, cloud resources, and networks (e.g., AWS, Azure, Linux)
* Writing compliance documentation (access logs, audit trails)
* Implementing **access control, encryption, patching, and backup policies**
* Meeting compliance requirements (HIPAA, FedRAMP, FISMA, etc.)

---

# 📚 NIST Essentials You Should Know

### 1. 🛡️ NIST 800-53 — *Security and Privacy Controls*

This is the most important for system administrators and DevOps folks.

**What it is:**
A catalog of **technical and administrative security controls** used by federal agencies — but adopted widely in healthcare, finance, and cloud platforms.

**Examples of Controls (with mapping):**

| Control ID | What It Means            | Practical Example                             |
| ---------- | ------------------------ | --------------------------------------------- |
| AC-2       | Account Management       | Create/remove users via Ansible scripts       |
| AU-2       | Audit Events             | Log sudo activity and SSH logins              |
| CM-2       | Baseline Config          | Use Terraform to enforce system configuration |
| SC-12      | Cryptographic Protection | Use TLS 1.2+ for HTTPS and encrypt S3 buckets |
| IR-4       | Incident Handling        | Define steps for reacting to a breach in SOP  |

📄 Learn more: [NIST 800-53 Controls (GitHub mirror)](https://github.com/usnistgov/NIST-800-53-Controls)

---

### 2. 🧭 NIST Cybersecurity Framework (NIST CSF)

**What it is:**
A high-level **security management framework** to help organizations identify and reduce cybersecurity risk.

**It’s structured in 5 core functions:**

| Function | Description              | Example                             |
| -------- | ------------------------ | ----------------------------------- |
| Identify | Know your assets, risks  | Inventory all EC2 and S3 buckets    |
| Protect  | Safeguard systems        | Enable MFA and IAM policies         |
| Detect   | Monitor for breaches     | Set up AWS GuardDuty or SIEM        |
| Respond  | Take action on incidents | Run a playbook during a DDoS attack |
| Recover  | Restore operations       | Restore RDS from backup snapshot    |

🎯 Great for **DevOps SREs building cloud security policies**.

---

### 3. 🧮 NIST SP 800-171 — *Protecting CUI (Controlled Unclassified Information)*

**What it is:**
A smaller set of NIST 800-53 controls, focused on securing sensitive but unclassified federal data — often used in **contracting** and **supply chain systems**.

If your team hosts or manages customer data in AWS, GCP, Azure, or government clouds, **this becomes very relevant**.

---

# 🛠️ How DevOps & SysAdmins Use NIST

### ✅ Example 1: Secure EC2 & Linux Systems with NIST 800-53

```yaml
# Ansible role snippet (mapping to AC-2 and CM-2)
- name: Create secure Linux user
  ansible.builtin.user:
    name: devopsadmin
    state: present
    groups: sudo
    shell: /bin/bash

- name: Ensure SSH key authentication is used
  ansible.builtin.lineinfile:
    path: /etc/ssh/sshd_config
    regexp: '^PasswordAuthentication'
    line: 'PasswordAuthentication no'
```

### ✅ Example 2: Define SOP using NIST CSF principles

```md
## SOP: Secure AWS S3 Buckets

- Enable versioning
- Block public access
- Apply bucket policy to allow only IAM roles from org account
- Use server-side encryption (AES-256)
```

---

# 📂 Suggested Learning Path

Here’s how you can start organizing your NIST knowledge in your GitHub repo:

```bash
mkdir -p NIST/800-53 NIST/CSF NIST/Examples

# Start with these files
touch NIST/800-53/README.md
touch NIST/CSF/NIST_Cybersecurity_Framework.md
touch NIST/Examples/Linux_Hardening.md
```

## Sample `NIST/800-53/README.md` Contents

```markdown
# NIST 800-53 for DevOps & SysAdmins

## Key Control Families
- Access Control (AC)
- Audit and Accountability (AU)
- Configuration Management (CM)
- Contingency Planning (CP)
- System and Communications Protection (SC)
```

---

## 🎯 Bonus: Mapping Tools

| Tool                      | Use                                             |
| ------------------------- | ----------------------------------------------- |
| OpenSCAP                  | Scan for compliance against NIST/PCI/DISA STIGs |
| AWS Config / Azure Policy | Cloud-native policy enforcement                 |
| Ansible Lockdown roles    | Apply NIST/CIS STIGs to RHEL, Ubuntu, Windows   |

---

## 🔚 Summary

* **NIST 800-53** = specific, detailed controls (great for hardening systems)
* **NIST CSF** = big picture framework (great for planning security posture)
* **NIST 800-171** = simplified set for handling sensitive but unclassified data

---

Would you like me to now:

* Build an Ansible hardening role mapped to NIST?
* Show NIST vs ISO control comparisons?
* Generate NIST audit checklist templates?
