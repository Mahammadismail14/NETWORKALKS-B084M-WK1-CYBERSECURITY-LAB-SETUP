# NETWORKALKS-B084M-WK1-CYBERSECURITY-LAB-SETUP
My Cybersecurity Lab Setup

# 🖥️ Cybersecurity Lab Setup
**NetworkWalks | Batch B084M | Week 1**

---

## 📌 What is this project?

I built an isolated virtual pentesting lab on my laptop using VirtualBox and Kali Linux. The goal was to create a safe environment where I can practice hacking tools and techniques without affecting my real machine or network.

---

## ⚙️ My Lab Configuration

| Component | Details |
|---|---|
| Host OS | Windows 10 |
| Hypervisor | VirtualBox 7.x |
| Security OS | Kali Linux 2026.x |
| Kali RAM | 2048 MB |
| Network Type | NAT Network |
| Network Address | 10.0.2.0/24 |
| Kali IP | 10.0.2.2/24 |
| Gateway | 10.0.2.1 |
| DNS | 8.8.8.8 |

---

## 🪜 What I Did

**1. Installed VirtualBox**
Downloaded from virtualbox.org and set it up as the hypervisor.

**2. Created a NAT Network**
Set up a private NAT Network (`10.0.2.0/24`) so future VMs can talk to each other inside the lab.

![NAT Network](2-nat-network.png)

**3. Imported Kali Linux**
Downloaded the official Kali VM and imported it into VirtualBox.

![Kali Imported](3-screenshot.png)

**4. Set Static IP**
```bash
sudo nmcli con mod "Wired connection 1" \
  ipv4.addresses 10.0.2.2/24 \
  ipv4.gateway 10.0.2.1 \
  ipv4.dns 8.8.8.8 \
  ipv4.method manual
sudo nmcli con up "Wired connection 1"
```
![Network Config](4-network-config.png)

**5. Took a Clean Snapshot**
Saved a baseline snapshot before doing anything else — so I can restore anytime.

![VirtualBox](1-virtualbox-setup.png)

---

## ✅ Verification

```bash
ip a              # confirmed 10.0.2.2/24
ping 10.0.2.1     # gateway reachable
ping 8.8.8.8      # internet working
nmap --version    # nmap ready
```

---

## 🐞 Issues I Faced

**Internet stopped after static IP**
Fixed with:
```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo reboot
```

**VT-x Error**
Went into BIOS → enabled Intel VT-x → restarted → worked.

---

## 💡 What I Learned

- Difference between NAT and NAT Network in VirtualBox
- How to set static IP using `nmcli` in Kali Linux
- Why snapshots are important before any testing
- How to document a cybersecurity project professionally

---

## 🔐 Ethical Use

This lab is for educational purposes only. All testing is done on systems I own inside an isolated environment.

---

## 👤 Author

**Katlapudi Mahammad Ismail**
B.Tech Cybersecurity | Gates Institute of Technology (2023–2027)
Batch B084M | NetworkWalks Academy

linkedin : https://www.linkedin.com/in/muhammad-ismail-03743b387
