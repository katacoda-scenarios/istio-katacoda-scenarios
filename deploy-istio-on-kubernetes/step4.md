To showcase Istio, a BookInfo web application has been created. This sample deploys a simple application composed of four separate microservices which will be used to demonstrate various features of the Istio service mesh.

When deploying an application that will be extended via Istio, the Kubernetes YAML definitions are extended via _kube-inject_. This will configure the services proxy sidecar (Envoy), Mixers, Certificates and Init Containers.

`kubectl apply -f <(istioctl kube-inject -f istio/bookinfo/bookinfo.yaml)`{{execute}}

## Check Status

`kubectl get pods`{{execute}}

When the Pods are starting, you may see initiation steps happening as the container is created. This is configuring the Envoy sidebar for handling the traffic management and authentication for the application within the Istio service mesh.

Once running the application can be accessed via the path _/productpage_.

https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage

The ingress routing information can be viewed using `kubectl describe ingress`{{execute}}

The architecture of the application is described in the next step.
