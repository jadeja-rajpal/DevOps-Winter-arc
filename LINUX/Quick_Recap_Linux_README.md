<div align="center">

# ❄️ DEVOPS WINTER ARC
## 90 DAYS CHALLENGE
# 🐧 LINUX TASKS

**Linux Enterprise Project — 7 hands-on tasks that take a bare server to production-ready**

![Linux](https://img.shields.io/badge/Linux-Ubuntu_22.04%2F24.04-E95420?logo=ubuntu&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-Automation-4EAA25?logo=gnubash&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-Reverse_Proxy-009639?logo=nginx&logoColor=white)
![systemd](https://img.shields.io/badge/systemd-Services-2E74B5)
![LVM](https://img.shields.io/badge/LVM-Storage-6A4C93)
![Tasks](https://img.shields.io/badge/Tasks-7-C2185B)
![Status](https://img.shields.io/badge/Status-In_Progress-FFB74D)

*Learn → Build → Break → Fix → Automate → Explain*

</div>

---

## 🎯 The Mission

You have just been handed a **brand-new Linux server**. Your job is to take it from bare to production-ready:

secure it → run an app on it → put Nginx in front → give it real storage → break it on purpose → investigate what happened → automate the checks.

**Seven tasks. One server. By the end you will have a story to tell in every Linux interview.**

---

## 🗺️ How It All Fits Together

```text
   You (laptop)
      |  SSH key only         <- Task 1: hardening
      v
+----------------------------------------------+
|  LINUX SERVER                                |
|                                              |
|  Nginx :80 --proxy--> App :8000              |
|  (Task 3)             (Task 2: systemd)      |
|                                              |
|  /data on LVM         <- Task 4: storage     |
|                                              |
|  logs: journalctl, nginx, app                |
|        (Task 6: investigate)                 |
|                                              |
|  healthcheck.sh via cron   (Task 7)          |
|  break it and fix it       (Task 5)          |
+----------------------------------------------+
```

---

## ✅ The 7 Tasks at a Glance

| # | Task | Core skills | Difficulty | Time |
|---|------|-------------|:----------:|:----:|
| 1 | 🔐 [Linux Server Setup & Hardening](#task-1--linux-server-setup--hardening) | Users, groups, SSH keys, sudo, permissions | ★★☆☆☆ | 1–2 h |
| 2 | ⚙️ [Application + systemd](#task-2--application--systemd) | Deployment, unit files, service control | ★★☆☆☆ | 1–2 h |
| 3 | 🌐 [Nginx Reverse Proxy](#task-3--nginx-reverse-proxy) | proxy_pass, headers, access/error logs | ★★☆☆☆ | 1–2 h |
| 4 | 💽 [Storage & LVM](#task-4--storage--lvm) | Disks, LVM, filesystems, `/etc/fstab`, resize | ★★★☆☆ | 2 h |
| 5 | 🔥 [Production Troubleshooting](#task-5--production-troubleshooting) | CPU, memory, disk, `top`, `free`, `df`, `iostat` | ★★★☆☆ | 2 h |
| 6 | 🕵️ [Log Investigation](#task-6--log-investigation) | `journalctl`, `grep`, `awk`, timelines | ★★★☆☆ | 2 h |
| 7 | 🤖 [Bash Automation: Health Check](#task-7--bash-automation-server-health-check) | Bash, `awk`, `systemctl`, `curl`, cron | ★★★★☆ | 2–3 h |

> Times are suggestions — go at your own pace.

---

## 🧰 Prerequisites

- **A Linux server** — Ubuntu 22.04 or 24.04 on VirtualBox, Multipass, or a small cloud instance. Commands are Ubuntu/Debian; RHEL-family differences are noted in the task hints.
- **A second virtual disk** for Task 4 (or use a loop device).
- **An SSH client** on your laptop.
- **Git** to track your configs, scripts and notes.
- A **test VM you can safely break** — Task 5 deliberately stresses the machine.

---

## 🚀 Quick Start

```bash
# 1. Clone this repo
git clone https://github.com/<your-username>/linux-enterprise-project.git
cd linux-enterprise-project

# 2. Create your working folders (see "Suggested Repo Structure" below)
mkdir -p tasks/{01-setup-hardening,02-app-systemd,03-nginx-proxy,04-storage-lvm,05-troubleshooting,06-log-investigation,07-bash-automation}

# 3. Start with Task 1 and work in order — each task builds on the last
```

**Ground rules**

1. Use a real VM or cloud server — don't just read.
2. Type every command yourself and read the output.
3. Break things on purpose, then fix them.
4. Save notes, configs and screenshots for every task.

---

## 📋 Task Details

### Task 1 — Linux Server Setup & Hardening

**Goal:** Turn a fresh server into a locked-down host: named admin users, key-only SSH, no root login, and sensible permissions.

- Users and groups (admin user + service user)
- SSH key authentication
- `sudo` rules via `/etc/sudoers.d/`
- Permissions on application directories
- Disable root login and password authentication
- Firewall (SSH only)

**✅ Done when:** root SSH login is refused · password login is refused · key login works · `id` and `sudo -l` show the intended groups and rules.

**📦 Deliverable:** a note listing every SSH config change and why you made it.

---

### Task 2 — Application + systemd

**Goal:** Deploy a small web app and make it behave like a real service — starts on boot, restarts on failure, easy to debug.

- Deploy an app with a `/health` endpoint into `/opt/myapp`
- Write a `systemd` unit file and run it as the service user
- Practise start, stop, restart, status
- Break the unit on purpose and fix each failure
- `kill -9` the process and watch systemd bring it back

**✅ Done when:** `systemctl is-active myapp` prints `active` · the health endpoint responds · the app survives `kill -9` and a reboot.

**📦 Deliverable:** your unit file plus a table of failures you caused and the exact error each produced.

---

### Task 3 — Nginx Reverse Proxy

**Goal:** Put Nginx in front of the app so users hit port 80 while the app stays private on localhost — then learn to read what Nginx tells you.

- Server block with `proxy_pass` to `127.0.0.1:8000`
- Proxy headers (`Host`, `X-Real-IP`, `X-Forwarded-For`, `X-Forwarded-Proto`)
- Test with `nginx -t`, reload without dropping connections
- Analyse the access log: status codes, top IPs, slow requests
- Stop the app, observe the **502**, find it in the error log

**✅ Done when:** the app works through Nginx · the app port isn't exposed externally · you can explain the top status codes in your log.

**📦 Deliverable:** your server block and the access-log analysis.

---

### Task 4 — Storage & LVM

**Goal:** Add a disk, build a logical volume, mount it permanently, then grow it without downtime.

- Add a disk and find it with `lsblk`
- `pvcreate` → `vgcreate` → `lvcreate`
- Create a filesystem and mount it at `/data`
- Persist the mount with a **UUID** entry in `/etc/fstab` (test with `mount -a`!)
- Add a second disk, extend the VG and LV, grow the filesystem

**✅ Done when:** `/data` survives a reboot · `df -h` shows the larger size after expansion · you can explain PV → VG → LV in one sentence.

**📦 Deliverable:** before-and-after `lsblk` and `df -h` output.

---

### Task 5 — Production Troubleshooting

**Goal:** Cause real resource problems on purpose, then find the culprit using only command-line tools.

- Simulate **high CPU** → find the process and read the load average
- Simulate **memory pressure** → confirm it and check for OOM kills
- Fill a **disk** (and run out of **inodes**) → find what is consuming space
- Write down symptom → command → root cause → fix for each

**✅ Done when:** you can name the exact PID behind each problem · you found an OOM message · you located the biggest directory · everything is cleaned up.

**📦 Deliverable:** a table of scenario, commands used, root cause and fix.

---

### Task 6 — Log Investigation

**Goal:** Investigate an incident like a detective — find the errors, pin down exactly when it began, and explain why.

- Introduce a failure at a time you note privately
- Investigate blind with `journalctl` (filter by unit, priority, time window)
- Search app and Nginx logs for the first error; count errors per minute
- Correlate app errors, Nginx 5xx responses and systemd restarts
- Write an incident timeline

**✅ Done when:** you can state the exact start time · name the root cause (not just the symptom) · connect at least three log sources.

**📦 Deliverable:** a mini postmortem — timeline, root cause, fix, and one improvement to detect it sooner.

---

### Task 7 — Bash Automation: Server Health Check

**Goal:** Write a script that reports on CPU, memory, disk, key services and the app itself — and tells automation whether things are healthy.

- CPU via load average vs core count
- Memory and disk as percentages against thresholds
- Service checks with `systemctl is-active`
- App check with `curl` and the HTTP status code
- Timestamped logging and a meaningful **exit code**
- Schedule with cron and test by breaking each check

**✅ Done when:** it prints OK when healthy · stopping nginx triggers a FAIL and a non-zero exit · high disk usage triggers the warning · cron keeps the log growing.

**📦 Deliverable:** your finished `healthcheck.sh` and a log excerpt showing OK and FAIL runs.

---

## 📁 Suggested Repo Structure

```text
linux-enterprise-project/
├── README.md
├── tasks/
│   ├── 01-setup-hardening/
│   │   ├── notes.md              # what you did and why
│   │   └── sshd_config.snippet
│   ├── 02-app-systemd/
│   │   ├── myapp.service
│   │   └── failures-table.md
│   ├── 03-nginx-proxy/
│   │   ├── myapp.conf
│   │   └── log-analysis.md
│   ├── 04-storage-lvm/
│   │   ├── commands.md
│   │   └── before-after.txt
│   ├── 05-troubleshooting/
│   │   └── scenarios.md
│   ├── 06-log-investigation/
│   │   └── postmortem.md
│   └── 07-bash-automation/
│       ├── healthcheck.sh
│       └── sample-log.txt
└── screenshots/
```

**Tip:** for each task, write a short `notes.md` with *Goal → What I did → What broke → What I learned*. That becomes your interview story.

---

## 📈 Progress Tracker

- [ ] **Task 1** — Server hardened, key-only SSH, no root login
- [ ] **Task 2** — App running as a systemd service, survives `kill -9` and reboot
- [ ] **Task 3** — Nginx proxying the app, 502 reproduced and diagnosed
- [ ] **Task 4** — LVM volume mounted via fstab and expanded online
- [ ] **Task 5** — CPU, memory and disk problems found and fixed
- [ ] **Task 6** — Incident timeline and postmortem written
- [ ] **Task 7** — Health-check script working under cron
- [ ] 🏆 **Capstone** — Rebuild the whole server from your notes

---

## 🎤 Interview Questions This Project Prepares You For

| Task | Questions |
|:----:|-----------|
| 1 | How do you secure SSH on a production server? · What's the difference between `chmod 755` and `750`? |
| 2 | A service keeps restarting — how do you find out why? · `Restart=on-failure` vs `Restart=always`? |
| 3 | What is a reverse proxy and why use one? · Users get 502 Bad Gateway — what do you check, in order? |
| 4 | How do you extend a filesystem without downtime using LVM? · What happens if `/etc/fstab` has a bad entry? |
| 5 | The server is slow — walk me through your first five commands. · What does load average mean? |
| 6 | How do you work out when an incident started? · How do you read the logs of a single systemd service? |
| 7 | How would you schedule this script and alert on failure? · Why do exit codes matter in automation? |

---

## 🏆 Capstone Challenge

**Destroy the server and rebuild everything from your notes — without looking at the hints.** Time yourself.

Then go one step further: automate the whole rebuild with Bash today, and with **Ansible** and **Terraform** later in the Winter Arc.

---

## 🔗 Part of the DevOps Winter Arc

This project is the deep-dive version of **Week 1** and **Project 4 (Hardened Linux Server & Automated Deploy)** in the 90-day DevOps Winter Arc roadmap:

```text
Linux → AWS → Docker → CI/CD → Kubernetes → EKS → Terraform → GitOps → Observability → DevSecOps → Interview Sprint
```

Finish these seven tasks before Week 2 and every later tool will make far more sense.

---

## 🛡️ Safety Notes

- Run the stress and disk-filling exercises **only on a disposable VM**.
- Before changing SSH settings, keep one session open and test from a second terminal.
- Always test `/etc/fstab` with `sudo mount -a` before rebooting.
- Never commit private keys, passwords or real server IPs to this repo.

---

## 🤝 Contributing

Found a better hint or a distro-specific fix? Open an issue or pull request.

## 📄 License

Add your preferred license here (for example MIT).

---

<div align="center">

**❄️ Learn → Build → Break → Fix → Automate → Explain ❄️**

*If this helped you, give it a ⭐ and share it with someone starting their DevOps journey.*

</div>
