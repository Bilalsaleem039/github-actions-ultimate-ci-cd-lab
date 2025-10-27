# github-actions-ultimate-ci-cd-lab
Starter repo for learning GitHub Actions CI/CD with Docker + Docker Hub + Kubernetes (minikube/k3s).

## Quick local steps

1. Install Docker, kubectl, and minikube (or k3s).
2. Start minikube: `minikube start`.
3. Build image locally and load into minikube:
   ```bash
   eval $(minikube docker-env)
   docker build -t sample-app:local .
   kubectl apply -f k8s/
   kubectl get svc
   ```

## GitHub Actions

Workflows are in `.github/workflows/`:
- `ci.yml` — lint, test, scan
- `build.yml` — build + push to Docker Hub (runs on push to `main`)
- `deploy.yml` — deploy to k8s after build completes

## Secrets (add in GitHub repo Settings → Secrets)
- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`
- `KUBECONFIG_DATA` (optional; base64 kubeconfig for remote cluster)
- `DISCORD_WEBHOOK_URL` (optional)
