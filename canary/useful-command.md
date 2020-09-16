kubectl --namespace=production get events -w

export SERVICE_IP=\$(kubectl --namespace=production get service/app-lb --output=json | jq -r '.status.loadBalancer.ingress[0].ip')

curl http://\$SERVICE_IP/
