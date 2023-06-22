# Looking at resources

`kubectl get pods -n gpn-mizzou-eecs`
`kubectl get deployments`
`kubectl get jobs`
`kubectl get pods`
`kubectl get services`

To get all nodes in the system
`kubectl get nodes`

Include the GPU column in the list
`kubectl get nodes -L nvidia.com/gpu.product`

Include GPU column and limit to nodes that have `nvidia.com/gpu.product` set to true.
`kubectl get nodes -L nvidia.com/gpu.product -l nvidia.com/gpu.product`

Include GPU column and limit to nodes that have `nvidia.com/gpu.product` set to a specific string.
`kubectl get nodes -L nvidia.com/gpu.product -l nvidia.com/gpu.product=='NVIDIA-GeForce-RTX-3090'`
`kubectl get nodes -L nvidia.com/gpu.product -l nvidia.com/gpu.product=='NVIDIA-GeForce-RTX-2080-Ti'`
`kubectl get nodes -L nvidia.com/gpu.product -l nvidia.com/gpu.product=='NVIDIA-GeForce-GTX-1080-Ti`

## Launching a Pod

`kubectl get events --sort-by=.metadata.creationTimestamp`
`kubectl get pod -o wide pod-<username>`

`kubectl exec -it <pod-name> -- /bin/bash`
`kubectl exec -it <pod-name> -c <container> -- /bin/bash`

`kubectl delete -f my_pod.yml` 

# Setting up Storage

# Deployments

`kubectl create -f depl.yml`

We can check that our deployment is running with `kubectl get deployments`, and since a deployment creates pods for us we can  check that our pods are running with `kubectl get pods`. This should output something similar to

```
```

Look at the deployment with
`kubectl get deployments`

Look at pods inside the deployment
`kubectl get pods`
`kubectl get pods -o wide`	shows local (inside the network) IP.

The deployment assigns a specific hash to each pod within, so that the name of the pod takes the form `dep-<username>-<hash>`. Using these names associated to each pod in the deployment, we can see the details of each pod by doing

`kubectl get pod -o wide dep-<username>-<hash>`

`kubectl exec -it dep-<username>-<hash> -- /bin/bash`

Deleting the pod

`kubectl delete pod dep-<username>-<hash>`

Once deleted, running `kubectl get pod -o wide dep-<username>-<hash>` will show that the pod is gone. However, `kubectl get pods` will show there is a new pod running! 

To finally delete the deployment we can run

`kubectl delete -f depl.yml`


# Ingress
 `kubectl create -f ingress.yml`
 
 ```
 ```
 
The pod can be accessed via `https://<username>.nrp-nautilus.io`


# Jobs

`k get pods --selector=job-name=test-job`