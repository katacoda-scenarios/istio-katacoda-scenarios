With Istio's insight into how applications communicate, it can generate profound insights into how applications are working and performance metrics.

## Generate Load

Make view the graphs, there first needs to be some traffic. Execute the command below to send requests to the application.

`
while true; do
  curl -s https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage > /dev/null
  echo -n .;
  sleep 0.2
done
`{{execute}}

## Access Dashboards

With the application responding to traffic the graphs will start highlighting what's happening under the covers.

## Grafana

The first is the Istio Grafana Dashboard. The dashboard returns the total number of requests currently being processed, along with the number of errors and the response time of each call.

https://[[HOST_SUBDOMAIN]]-3000-[[KATACODA_HOST]].environments.katacoda.com/dashboard/db/istio-dashboard

As Istio is managing the entire service-to-service communicate, the dashboard will highlight the aggregated totals and the breakdown on an individual service level.

## Zipkin

Zipkin provides tracing information for each HTTP request. It shows which calls are made and where the time was spent within each request.

https://[[HOST_SUBDOMAIN]]-9411-[[KATACODA_HOST]].environments.katacoda.com/zipkin/?serviceName=productpage

Click on a span to view the details on an individual request and the HTTP calls made. This is an excellent way to identify issues and potential performance bottlenecks.

## Service Graph

As a system grows, it can be hard to visualise the dependencies between services. The Service Graph will draw a dependency tree of how the system connects.

https://[[HOST_SUBDOMAIN]]-8088-[[KATACODA_HOST]].environments.katacoda.com/dotviz


Before continuing, stop the traffic process with <kbd>Ctrl</kbd>+<kbd>C</kbd>
