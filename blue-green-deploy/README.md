# kubectl8s blue-green deploy sample

## preparation
export IP=127.0.0.1

## create current production blue env - version1
kubectl apply -f blue-deploy.yml
kubectl apply -f blue-service.yml

## check status
kubectl get all
kubectl describe svc hello-service
curl \$IP:31001

## create green deployment
kubectl apply -f green-deploy.yml
kubectl get pod -w

## monitor production service
while true; do curl \$IP:31001; echo; sleep 1; done

## cutover service
kubectl apply -f green-service.yml

## fallback if have problem
kubectl apply -f blue-service.yml

## destroy previous env if deploy is successful
kubectl delete deploy/blue-deploy

## destroy all env
kubectl delete deploy/green-deploy
kubectl delete services/hello-service





