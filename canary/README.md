alias k=kubectl

k apply -f prod-deploy.yml --record
k apply -f hello-service.yml

export IP=10.97.82.177
for i in `seq 1 10`; do curl http://\$IP:31000/; echo; sleep 1; done

k apply -f canary-deploy.yml
for i in `seq 1 10`; do curl http://\$IP:31000/; echo; sleep 1; done

k set image deploy/prod-deploy k8s-demo=mikeqiu2011/node-hostname:v2 --record

k rollout status deploy prod-deploy

k rollout history
k rollout undo deploy prod-deploy --to-revision=2
