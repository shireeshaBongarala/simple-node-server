1. Create a namespace `development` 
`kubectl create -f namespace-dev.json`

2. Create a similar one for `prod` namespace as well

3. List the config
`kubectl config view`

4. Attach the namespace to the cluster `dind`

    For dev,
`kubectl config set-context dind-dev --namespace=development --cluster=dind --user=dind-dev-user` <br/>
   For prod, <br/>
  `kubectl config set-context dind-prod --namespace=prod --cluster=dind --user=dind-prod-user`<br/>

 5. Get current context
`kubectl config current-context`

6. Use context `dind-dev`
`kubectl config use-context dind-dev`

7. Create some pods on this cluster:
`kubectl run snowflake --image=kubernetes/server_hostname replicas=2`  <br/>
`kubectl get deployment`<br/>
`kubectl get pods -l run=snowflake`

8. Use context `dind-prod`
`kubectl config use-context dind-prod`

9. Create some pods on this cluster:
`kubectl run cattle --image=kubernetes/server_hostname replicas=5`  <br/>
`kubectl get deployment`<br/>
`kubectl get pods -l run=cattle`
