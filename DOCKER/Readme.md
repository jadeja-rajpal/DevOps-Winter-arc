<div align="center">

# ❄️ DevOps Winter Arc Challenge
## Week 2 · Days 1–7 — Docker

*Go from "what is a container?" to a build → scan → push → deploy pipeline.*

![Docker](https://img.shields.io/badge/Docker-Containers-2496ED?logo=docker&logoColor=white)
![Compose](https://img.shields.io/badge/Docker-Compose-0DB7ED?logo=docker&logoColor=white)
![Trivy](https://img.shields.io/badge/Trivy-Security_Scan-1904DA)
![GitHub Actions](https://img.shields.io/badge/GitHub-Actions-2088FF?logo=githubactions&logoColor=white)
![Days](https://img.shields.io/badge/Days-7-2E74B5)
![Projects](https://img.shields.io/badge/Projects-10-6A4C93)

</div>

---

## 🔗 Start here

| | Link |
|---|---|
| 🎬 **Docker session video (YouTube)** | 👉 `https://youtu.be/TjnC_Qrd5_M?si=J_YDdHZ3JNZmsLRz` |
| 📺 **Channel: DevOps Jadeja** | [youtube.com/@Devops_jadeja](https://www.youtube.com/@Devops_jadeja) |
| 📘 **Full Week 2 document** | 👉 `https://docs.google.com/document/d/1aDsPSicMd173usS6UzDxeSQ7iLfVrz7B/edit?usp=sharing&ouid=104855601374610993853&rtpof=true&sd=true` *(will be updated later)* |

> **Watch the Docker session first.** It explains most of the concepts used below, so the commands and tasks make far more sense.

**How to learn each day:** 📺 Watch → 📖 Read the guide → 💻 Do the task on a real VM → ✅ Tick it off.

---

## 🗓️ Day-by-day: what you will find

| Day | Pillar | What you learn | 🔥 Task / deliverable |
|:---:|--------|----------------|----------------------|
| **1** | 🐳 Docker Fundamentals | Images, containers, registries, Docker Engine, CLI | Run Nginx, then build your own image → **your web server in a container** |
| **2** | 📝 Dockerfile Deep Dive | `FROM` `RUN` `COPY` `ADD` `WORKDIR` `ENV` `ARG` `EXPOSE` `CMD` `ENTRYPOINT`, layer caching | Containerize a Node/Python app, pass env vars, prove caching → **reusable Dockerfile** |
| **3** | 🏗️ Multi-Stage Builds | Build vs runtime stages, small images, non-root user | Single-stage vs multi-stage, compare sizes → **production-style image** |
| **4** | 💾 Storage & Networking | Volumes, bind mounts, bridge networks, port mapping, DNS | Postgres with a volume + app on a custom network → **app connected to a separate service** |
| **5** | 🎼 Docker Compose | Services, `depends_on`, health checks, `.env`, restart policies | Flask + Postgres + Redis → **full stack with one command** |
| **6** | 🛡️ Security & Optimization | Trivy, trusted bases, secrets, resource limits, tagging | Scan, fix and harden an image → **smaller, scanned, safer image** |
| **7** | 🚀 Docker in CI/CD | Registries, immutable tags, GitHub Actions, deploy | Build → test → scan → push (SHA tag) → deploy → **automated pipeline** |

---

## 🧪 10 Hands-on projects

Build them in order. Each one is a repo (or folder) for your portfolio.

| # | Project | Day | Challenge |
|:-:|---------|:---:|-----------|
| 1 | Multi-Stage Dockerfile (Node.js) | 2–3 | Compare single vs multi-stage image size |
| 2 | Custom Nginx Web Server | 1 | Port mapping, custom config, health check |
| 3 | Python Flask REST API | 2 | Env-var config, non-root user |
| 4 | Persistent Database Container | 4 | Delete container, prove data persists |
| 5 | Full-Stack App with Compose | 5 | Networking, health checks, volume, `.env` |
| 6 | Docker Image Optimization Lab | 3–6 | Document before/after size and build time |
| 7 | Container Security Scanning | 6 | Fail on HIGH/CRITICAL, fix, rescan |
| 8 | Docker CI Pipeline | 7 | Lint, test, tag, scan on every push |
| 9 | Docker Hub / ECR Publishing | 7 | Commit-SHA tags, secure credentials, pull elsewhere |
| 10 | Container Monitoring & Troubleshooting | 4–7 | `docker stats`, logs, health checks, Prometheus/Grafana |

---

## 🧭 The progression

```text
Day 1  Can I run and inspect containers?
Day 2  Can I package my own app properly?
Day 3  Can I ship it small and safe?
Day 4  Can I keep data and connect containers?
Day 5  Can I run a whole stack with one command?
Day 6  Can I secure and optimize it?
Day 7  Can I automate build, scan, publish and deploy?
```

---

## 📘 What's in the full guide

For every day: 🎯 goal and key concepts · 📖 command tables (**command → what it does → DevOps use case**) · 🔥 hands-on task with steps, starter code and hints · ✅ "how to know you're done" · 🎤 interview questions.
Plus: all 10 projects with build steps, and a finish-line checklist.

---

## ✅ Progress tracker

- [ ] **Day 1** — Nginx running, `my-site:v1` built
- [ ] **Day 2** — Dockerfile, env vars, CMD vs ENTRYPOINT, cache proof
- [ ] **Day 3** — Multi-stage, non-root image, size table
- [ ] **Day 4** — Postgres volume persistence, custom network
- [ ] **Day 5** — Compose stack with health checks
- [ ] **Day 6** — Trivy before/after, hardened run
- [ ] **Day 7** — GitHub Actions pipeline pushing SHA-tagged image
- [ ] **Projects 1–10** — pushed to GitHub with README + screenshots

---

## 📁 Suggested repo layout

```text
winter-arc-week2-docker/
├── README.md
├── day1-docker-basics/
├── day2-dockerfile/
├── day3-multistage/
├── day4-storage-network/
├── day5-compose/
├── day6-security/
├── day7-cicd/          # .github/workflows/docker-ci.yml
└── projects/           # 01-multistage-node ... 10-monitoring
```

**Tip:** for each day write a short note: *Goal → What I did → What broke → What I learned.*

---

<div align="center">

**❄️ Learn → Build → Break → Fix → Explain ❄️**

</div>
