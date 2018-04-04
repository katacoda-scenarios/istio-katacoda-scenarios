Istio is installed in two parts. The first part involves the CLI tooling that will be used to deploy and manage Istio backed services. The second part configures the Kubernetes cluster to support Istio.

## Install CLI tooling

The following command will install the Istio 0.7.1 release.

`curl -L http://assets.joinscrapbook.com/istio/getLatestIstio | sh -`{{execute}}

After it has successfully run, add the bin folder to your path.

`export PATH="$PATH:/root/istio-0.7.1/bin"`{{execute}}

## Configure Istio

The core components of Istio are deployed via _istio.yaml_.

`kubectl apply -f istio/istio.yaml`{{execute}}

This will deploy Pilot, Mixer, Ingress-Controller, and Egress-Controller, and the Istio CA (Certificate Authority). These are explained in the next step.

## Check Status

All the services are deployed as Pods. Once they're running, Istio is correctly deployed.

`kubectl get pods -n istio-system`{{execute}}
