<div align="center">

# ❄️ DevOps Winter Arc Challenge
## Week 1 · Days 1–7 — Linux + Networking + Git

*Become comfortable operating a Linux server.*

![Linux](https://img.shields.io/badge/Linux-Ubuntu-E95420?logo=ubuntu&logoColor=white)
![Networking](https://img.shields.io/badge/Networking-DNS%20%7C%20HTTP%20%7C%20SSH-6A4C93)
![Nginx](https://img.shields.io/badge/Nginx-Reverse_Proxy-009639?logo=nginx&logoColor=white)
![Git](https://img.shields.io/badge/Git-GitHub-F05032?logo=git&logoColor=white)
![Days](https://img.shields.io/badge/Days-7-2E74B5)

[![Watch on YouTube](https://img.shields.io/badge/▶_Watch_on_YouTube-DevOps__jadeja-FF0000?logo=youtube&logoColor=white)](https://www.youtube.com/@Devops_jadeja)

</div>

---

## 🎬 Start here: watch the videos first

> **Before you start the tasks, go through the videos on the DevOps Jadeja YouTube channel.**
> They explain most of the concepts used in this README, so the commands and tasks below will make far more sense.

### 👉 [youtube.com/@Devops_jadeja](https://www.youtube.com/@Devops_jadeja)

**Suggested way to learn each day:**

1. 📺 Watch the related video(s) for the day's topic.
2. 📖 Read the day's section below, then the command tables in the guide.
3. 💻 Do the hands-on task on a real VM.
4. ✅ Tick it off in the progress tracker.

---

## 🎯 What this week is about

Week 1 is not a list of Linux commands. It is the journey to becoming comfortable **operating a Linux server**: using it, securing it, understanding what runs on it, connecting to it, serving traffic from it, fixing it when it breaks, and keeping your work in Git.

Linux gets the strongest foundation in **Days 1–4**. Networking, DNS and HTTP come toward the end, and a Git/GitHub workflow closes the week.

---

## 🗓️ Day-by-day coverage and tasks

| Day | Pillar | What we cover | 🔥 Hands-on task |
|:---:|--------|---------------|------------------|
| **1** | 🗂️ Linux Fundamentals & Shell | Filesystem layout, navigation, `find`, `grep`, pipes, redirection, package management | **Build a Linux workspace:** create an app directory, organise files/logs/configs, search them, redirect output |
| **2** | 👤 Users, Permissions & Bash | Users, groups, `sudo`, `chmod`/`chown`, variables, `$PATH`, `.bashrc`, scripting | **User + permission setup:** shared app directory (devs write, others read-only), automated with a Bash script |
| **3** | ⚙️ Processes, Services & Logs | `ps`, `top`, signals, `systemctl`, `journalctl`, `/var/log` | **Troubleshoot a service:** start/stop it, find its PID, read logs, break it, fix it |
| **4** | 🌐 Networking + SSH | IP, subnets, ports, TCP vs UDP, `ss`, `curl`, SSH keys, `/etc/hosts` | **Connect & troubleshoot:** key-based SSH, hostname via `/etc/hosts`, find listening ports, firewall block vs stopped service |
| **5** | 🌍 DNS + HTTP/HTTPS + Nginx | `dig`, HTTP methods and status codes, TLS basics, Nginx reverse proxy | **Deploy an app behind Nginx:** app on `:3000`, Nginx on `:80`, hostname mapping, diagnose a 502 |
| **6** | 💾 Storage + Monitoring + Debugging | `df`, `du`, `free`, `lsblk`, `mount`, `/etc/fstab`, resource debugging | **Fix a server issue:** mount a disk via `fstab`, fill it up, find the space hog, verify after reboot |
| **7** | 🔀 Git/GitHub + Production Challenge | `commit`, `push`, branches, merge, pull requests, `.gitignore` | **Mini production project:** push your project to GitHub, open a PR, then fix a deliberately broken Linux/Nginx setup |

---

## 🧭 The progression

```text
Day 1  Can I use Linux?
Day 2  Can I manage access and automate?
Day 3  Can I understand what is running, and why it is failing?
Day 4  Can I connect to and troubleshoot a server?
Day 5  Can I understand how traffic reaches an application?
Day 6  Can I troubleshoot a real server problem?
Day 7  Can I put my work into Git and handle a production-style problem?
```

---

## 📘 What's in the guide

The full Word guide includes, for every day:

- 🎯 Goal and key concepts
- 📖 Command tables with **command → what it does → DevOps use case**
- 🔥 A hands-on task with steps, starter commands and hints
- ✅ A "how to know you're done" checklist and a deliverable
- 🎤 Interview questions the day prepares you for

---

## ✅ Progress tracker

- [ ] **Day 1** — Linux workspace built
- [ ] **Day 2** — Users, permissions and `setup.sh` done
- [ ] **Day 3** — Service created, broken and fixed
- [ ] **Day 4** — SSH keys, hosts entry and port checks done
- [ ] **Day 5** — App running behind Nginx, 502 diagnosed
- [ ] **Day 6** — Disk mounted via `fstab`, space issue solved
- [ ] **Day 7** — Repo pushed, PR merged, incident fixed

---

## 📁 Suggested repo layout

```text
winter-arc-week1/
├── README.md
├── day1-workspace/
├── day2-users-bash/        # setup.sh
├── day3-service/           # demo-worker.service
├── day4-ssh-network/       # ssh config notes
├── day5-nginx/             # myapp server block
├── day6-storage/           # fstab line, before/after df -h
└── day7-incident/          # incident-notes.md
```

**Tip:** for each day, write a short note: *Goal → What I did → What broke → What I learned.*

---

## 🚀 Next up

**Week 2 — AWS Fundamentals:** IAM, VPC, EC2, ALB, Route53, S3, RDS and CloudWatch.

<div align="center">

**❄️ Learn → Build → Break → Fix → Explain ❄️**

</div>
