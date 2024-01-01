minikube start --network-plugin=cni --cni=calico 

kubectl label namespaces default namespacename=default --overwrite=true

 kubectl apply -f nginx-double.yaml -n default

kubectl apply -f allow.yaml 
kubectl get networkpolicies.crd.projectcalico.org

kubectl apply -f deny.yaml
kubectl get globalnetworkpolicies.crd.projectcalico.org

#check with k9s
kubectl exec -it  my-nginx1-74bc886dc-lgmwb -- curl 10.244.120.73 --max-time 1
kubectl exec -it  my-nginx2-66bfb6fcff-wlhvq -- curl 10.244.120.72 --max-time 1




