# Playwright_test
Playwright test experiments

## Run With Docker

```powershell
docker compose run --rm --build playwright
```

## Run With Local Kubernetes

Build the image first:

```powershell
docker build -t playwright-tests:local .
```

Run the Kubernetes Job:

```powershell
kubectl delete job playwright-tests --ignore-not-found
kubectl apply -f k8s/playwright-job.yaml
kubectl wait --for=condition=complete --timeout=180s job/playwright-tests
kubectl logs job/playwright-tests
```
