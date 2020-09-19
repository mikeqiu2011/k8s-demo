command example

```
alias k=kubectl
export IP=1.1.1.1

k apply -f blue-deploy.yml
k apply -f blue-service.yml
k get all
k describe svc hello-service
curl \$IP:31001
k apply -f blue-deploy.yml
k apply -f green-deploy.yml
k get pod -w

curl $IP:31001
k apply -f green-service.yml
curl $IP:31001
while true; do curl \$IP:31001; echo; sleep 1; done
```
