32 k apply -f blue-deploy.yml
33 k apply -f blue-service.yml
37 k get all
38 k describe svc hello-service
39 curl 10.96.102.222:31001
40 k apply -f blue-deploy.yml
41 k apply -f green-deploy.yml
42 k get pod -w

44 curl 10.96.102.222:31001
45 k apply -f green-service.yml
46 curl 10.96.102.222:31001
47 while true; do curl 10.96.102.222:31001; echo; sleep 1; done
