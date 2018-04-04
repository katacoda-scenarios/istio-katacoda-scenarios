While Service Graph displays a high-level overview of how systems are connected, a tool called Weave Scope provides a powerful visualisation and debugging tool for the entire cluster.

Using Scope it's possible to see what processes are running within each pod and which pods are communicating with each other. This allows users to understand how Istio and their application is behaving.

## Deploy Scope

Scope is deployed onto a Kubernetes cluster with the command `kubectl create -f 'https://cloud.weave.works/launch/k8s/weavescope.yaml'`{{execute}}

Wait for it to be deployed by checking the status of the pods using `kubectl get pods -n weave`{{execute}}

## Make Scope Accessible

Once deployed, expose the service to the public.

`
pod=$(kubectl get pod -n weave --selector=name=weave-scope-app -o jsonpath={.items..metadata.name})
kubectl expose pod $pod -n weave --external-ip="[[HOST_IP]]" --port=4040 --target-port=4040`{{execute}}

**Important:** Scope is a powerful tool and should only be exposed to trusted individuals and not the outside public. Ensure correct firewalls and VPNs are configured.

View Scope on port 4040 at https://[[HOST_SUBDOMAIN]]-4040-[[KATACODA_HOST]].environments.katacoda.com/

## Generate Load

Scope works by mapping active system calls to different parts of the application and the underlying infrastructure. Create load to see how various parts of the system now communicate.

`
while true; do
  curl -s https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage > /dev/null
  echo -n .;
  sleep 0.2
done
`{{execute}}
