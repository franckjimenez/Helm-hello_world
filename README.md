# Helm-hello_world


helm install helloworld-go-chart helloworld-go/ --values helloworld-go/values.yaml


export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services helloworld-go-chart)
export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
echo http://$NODE_IP:$NODE_PORT

helm delete helloworld-go-chart