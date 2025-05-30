How To install Promethus and grafana and Monitor Kubernetes Cluster

Step-1 Follow https://github.com/mrathoredevopsengineer/kubestarter.git to Install Kubernetes Cluster (Master & Worker Node) on VM.

Step-2
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
kubectl create namespace monitoring
helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring
kubectl get pods -n monitoring
kubectl get svc -n monitoring
kubectl expose service prometheus-kube-prometheus-prometheus --type=NodePort --target-port=9090 --name=prometheus-expose -n monitoring
kubectl expose service prometheus-grafana --type=NodePort --target-port=3000 --name=grafana-expose -n monitoring




