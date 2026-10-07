SET C ARCHITECTURE

Browser
   |
   v
Frontend (NodePort 30082)
   |
   v
Go API (ClusterIP)
   |
   v
PostgreSQL (ClusterIP)

Replace the placeholder Docker image names in the deployment YAML files
with the student's own Docker Hub images before applying the manifests.
