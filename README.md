I have done this using minikube cluster in the local environment.
Enabled network policy for blocking communication between different namespaces
Tested using a test-pod launched in feature1-namespace
############################################################################################

We can create separate namespaces each of the feature so that it can be isolated environments

We can deploy service A (n+1) and service B (n) in feature1-namespace. These two services i.e. service A (n+1) and service B (n) can communicate with each other being in same namespace. A curl command followed by service url should work.

We can deploy service A (n) and service B (n+1) in feature2-namespace These two services i.e. service A (n) and service B (n+1) can communicate with each other being in same namespace. A curl command followed by service url should work.

Now, to avoid communication between these two namespaces we can apply a network policy using plugin like calico (open source) denying all ingress traffic from other namespace.

If we are using helm chart, we can deploy all the resources together.

For deployment, we can install GitOps tool ArgoCD (Open source) so that we can enable continuous deployment in Kubernetes

##############################################################################################

helm install my-app-release my-app-chart
