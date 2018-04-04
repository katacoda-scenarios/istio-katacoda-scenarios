To collect and view metrics provided by Mixer, install Prometheus Grafana and ServiceGraph addons.

Prometheus gathers metrics from the Mixer. `kubectl apply -f istio/addons/prometheus.yaml`{{execute}}

Grafana produces dashboards based on the data collected by Prometheus. `kubectl apply -f istio/addons/grafana.yaml`{{execute}}

ServiceGraph delivers the ability to visualise dependencies between services. `kubectl apply -f istio/addons/servicegraph.yaml`{{execute}}

Zipkin offers distributed tracing. `kubectl apply -f istio/addons/zipkin.yaml`{{execute}}


## Check Status

As with Istio, these addons are deployed via Pods.

`kubectl get pods -n istio-system`{{execute}}
