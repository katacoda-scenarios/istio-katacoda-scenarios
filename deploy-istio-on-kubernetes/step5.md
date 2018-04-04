The BookInfo sample application deployed is composed of four microservices:

* The _productpage_ microservice is the homepage, populated using the details and reviews microservices.
* The _details_ microservice contains the book information.
* The _reviews_ microservice contains the book reviews. It uses the ratings microservice for the star rating.
* The _ratings_ microservice contains the book rating for a book review.

The deployment included three versions of the _reviews_ microservice to showcase different behaviour and routing:

* Version _v1_ doesn’t call the ratings service.
* Version _v2_ calls the ratings service and displays each rating as 1 to 5 black stars.
* Version _v3_ calls the ratings service and displays each rating as 1 to 5 red stars.

The services communicate over HTTP using DNS for service discovery. An overview of the architecture is shown below.

![BookInfo Architecture](https://katacoda.com/courses/istio/deploy-istio-on-kubernetes/assets/bookinfo-arch.png)

The source code for the application is available on [Github](https://github.com/istio/istio/tree/release-0.1/samples/apps/bookinfo/src)
