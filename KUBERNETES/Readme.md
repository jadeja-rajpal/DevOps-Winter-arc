# DevOps Winter Arc · Week 3: Kubernetes (kind)

Days 1–7 · 7 small hands-on tasks · 30% concepts + 70% hands-on

**Learn → Build → Break → Fix → Explain**

## 🎬 Start here: watch the video first

[▶ Watch: Kubernetes on kind (Week 3)](ADD_YOUR_YOUTUBE_VIDEO_LINK_HERE)

More videos: [youtube.com/@Devops_jadeja](https://youtube.com/@Devops_jadeja)

📄 Slides: [Week 3 Kubernetes deck](ADD_YOUR_DOCUMENT_LINK_HERE)

## The 7-day route

| Day | Topic | Task of the day |
|---|---|---|
| 1 | Kubernetes Fundamentals & kind | Create a 3-node kind cluster and run your first Pod |
| 2 | Deployments & Rollouts | Deploy 3 replicas, upgrade, break the release and roll back |
| 3 | Services & Networking | Call a backend by name, then open it on `localhost:30080` |
| 4 | Config, Secrets & Namespaces | Run the same image in dev and prod with different config |
| 5 | Storage & StatefulSets | Run Postgres, delete the Pod and prove the data survives |
| 6 | Health, Resources & Autoscaling | Autoscale an app under load with an HPA |
| 7 | Security, RBAC & Troubleshooting | Lock down a namespace, then fix 3 broken Pods |

## Repo structure

```text
week3-kubernetes/
├── kind-config.yaml        # one cluster for the whole week
├── day1-k8s-basics/
├── day2-deployments/
├── day3-services/
├── day4-config/
├── day5-storage/
├── day6-health-scaling/
├── day7-security-debug/
└── README.md
```

Each `dayN-*/` folder holds that day's YAML files, screenshots and a short README of the commands you used.

## Lab cluster

Everything runs on a local [kind](https://kind.sigs.k8s.io) cluster (Docker required, from Week 2):

```bash
kind create cluster --name winter-arc --config kind-config.yaml
```

## Progress

- [ ] Day 1: cluster + first Pod
- [ ] Day 2: Deployment, rollout, rollback
- [ ] Day 3: Services and NodePort
- [ ] Day 4: ConfigMap, Secret, namespaces
- [ ] Day 5: PVC and StatefulSet
- [ ] Day 6: probes, limits, HPA
- [ ] Day 7: RBAC and troubleshooting

## Not covered this week

Ingress, Helm, GitOps and NetworkPolicy. This week stays on core Kubernetes objects.
