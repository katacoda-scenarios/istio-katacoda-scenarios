One of the main features of Istio is its traffic management. As a Microservice architectures scale, there is a requirement for more advanced service-to-service communication control.

## User Based Testing

One aspect of traffic management is controlling traffic routing based on the HTTP request, such as user agent strings, IP address or cookies.

The example below will send all traffic for the user "jason" to the reviews:v2, meaning they'll only see the black stars.

`cat istio/bookinfo/route-rule-reviews-test-v2.yaml`{{execute}}

Similarly to deploying Kubernetes configuration, routing rules can be applied using _istioctl_.

`istioctl create -f istio/bookinfo/route-rule-reviews-test-v2.yaml`{{execute}}

Visit the [product page](https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage) and signin as a user jason (password jason)

## Traffic Shaping for Canary Releases

The ability to split traffic for testing and rolling out changes is important. This allows for A/B variation testing or deploying canary releases.

The rule below ensures that 50% of the traffic goes to reviews:v1 (no stars), or reviews:v3 (red stars).

`cat istio/bookinfo/route-rule-reviews-50-v3.yaml`{{execute}}

Likewise, this is deployed using _istioctl_.

`istioctl create -f istio/bookinfo/route-rule-reviews-50-v3.yaml`{{execute}}

_Note:_ The weighting is not round robin, multiple requests may go to the same service.

## New Releases

Given the above approach, if the canary release were successful then we'd want to move 100% of the traffic to reviews:v3.

`cat istio/bookinfo/route-rule-reviews-v3.yaml`{{execute}}

This can be done by updating the route with new weighting and rules.

`istioctl replace -f istio/bookinfo/route-rule-reviews-v3.yaml`{{execute}}

## List All Routes

It's possible to get a list of all the rules applied using `istioctl get routerules`{{execute}}
