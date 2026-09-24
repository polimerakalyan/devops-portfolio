Kubernetes Deployment
=====================

The application is deployed to Amazon EKS using Kubernetes.

Deployment Process
==================

1. Jenkins builds the Docker image.
2. Docker image is pushed to Amazon ECR.
3. Jenkins updates the Kubernetes deployment with the new image.
4. Kubernetes performs a rolling update.
5. Jenkins verifies the rollout status.

Deployment Command
==================

```bash
kubectl set image deployment/<deployment-name> \
  <container-name>=<ecr-image>:<image-tag> \
  -n <namespace>


Rollout Verification
==================

kubectl rollout status deployment/<deployment-name> \
  -n <namespace> \
  --timeout=180s
