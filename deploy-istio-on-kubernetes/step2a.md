The previous step deployed the Istio Pilot, Mixer, Ingress-Controller, and Egress-Controller, and the Istio CA (Certificate Authority).

* **Pilot** - Responsible for configuring the Envoy and Mixer at runtime.

* **Envoy** - Sidecar proxies per microservice to handle ingress/egress traffic between services in the cluster and from a service to external services. The proxies form a secure microservice mesh providing a rich set of functions like discovery, rich layer-7 routing, circuit breakers, policy enforcement and telemetry recording/reporting functions.

* **Mixer** - Create a portability layer on top of infrastructure backends. Enforce policies such as ACLs, rate limits, quotas, authentication, request tracing and telemetry collection at an infrastructure level.

* **Ingress/Egress** - Configure path based routing.

* **Istio CA** - Secures service to service communication over TLS. Providing a key management system to automate key and certificate generation, distribution, rotation, and revocation

The overall architecture is shown below.

![Istio Architecture](https://katacoda.com/courses/istio/deploy-istio-on-kubernetes/assets/istio-arch1.png)
