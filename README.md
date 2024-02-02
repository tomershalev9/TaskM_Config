# TaskM_Config!!


1. deploy eks cluster - terraform init/apply

2. to connect to the cluster :
   aws eks update-kubeconfig --region us-east-1 --name demo

3. deploy argo-cd-setup - terraform init/apply

4. port-forward the svc - kubectl port-forward svc/argocd-server -n argocd       8081:443
5. kubectl get secrets argocd-initial-admin-secret -o yaml -n argoc
   password
   echo enter_the_code_here | base64 -D
   or
   argocd admin initial-password -n argocd
   username:
   admin

6. deploy this yaml in argocd:

kubectl apply application.yaml
kubectl port-forward svc/tasksapp-svc 8080:8080 -n taskapp

7. deploy prometheus-setup terraform init/apply

port-forward the svc - kubectl port-forward svc/prometheus-operated 9090:9090 -n monitoring

                       kubectl port-forward svc/kube-prometheus-stackr-grafana 9091:80 -n monitoring

                    grafana username and password:
                    user: admin
                    pass: prom-operator
