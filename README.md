## Metallb_ON_PREMISE with Cilium and Nginx ingress controller 

### MetalLB is a load-balancer implementation for bare metal Kubernetes clusters, using standard routing protocols.

   MetalLB requires the following to function:

1) A Kubernetes cluster, running Kubernetes 1.13.0 or later, that does not already have network load-balancing functionality.

2) A cluster network configuration that can coexist with MetalLB.

3)  IPv4 addresses for MetalLB .

4) Depending on the operating mode, you may need one or more routers capable of speaking BGP.


### FOR EXAMPLE we have following setup 

1) A Kubernetes cluster: v1.15.1 (3 node cluster)

2)cluster network configuration : cilium 

kubectl create -f https://raw.githubusercontent.com/cilium/cilium/v1.5/examples/kubernetes/1.14/cilium.yaml



### Installing Metallb 

1) kubectl apply -f https://raw.githubusercontent.com/google/metallb/v0.8.1/manifests/metallb.yaml

(note: reference https://metallb.universe.tf/installation/)

This will deploy MetalLB to your cluster, under the metallb-system namespace. 

####The components in the manifest are:

1) The metallb-system/controller deployment.( This is the cluster-wide controller that handles IP address assignments.)

2) The metallb-system/speaker daemonset. (This is the component that speaks the protocol(s) of your choice to make the services reachable)

3)Service accounts for the controller and speaker, along with the RBAC permissions that the components need to function.




