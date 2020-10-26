# Awesome-sidecar
This list contains projects that can run as a sidecar in k8s, [learn more about sidecars](sidecar-explained.md)  
Please open a PR to add new project to the list.

## Service Mesh / Load Balancer
https://github.com/istio/proxy - part of Istio, uses envoy as a proxy sidecar  
https://github.com/linkerd/linkerd2-proxy - part of Linkerd, full proxy & load balancer implemented in Ruts  
https://github.com/minio/sidekick - High Performance HTTP Sidecar Load Balancer  

## Secrets
https://github.com/Talend/vault-sidecar-injector - part of HashiCorp Vault, for fetching secrets from Vault  

## Logs
https://github.com/h3poteto/fluentd-sidecar-injector  - ship log files using Fluentd  
https://github.com/infolinks/loggly-sidecar  - ship logs files using Loggly  

## Authentication and Authorisation
https://github.com/yahoojapan/athenz-client-sidecar - retrieve authentication and authorization credential from Athenz server  

## Leader Election
https://github.com/vapor-ware/k8s-elector - adds a leader election capability to a deployment 

## Dynamic Configuration
https://github.com/kiwigrid/k8s-sidecar - watch a config map and sends an HTTP request after a change  
https://github.com/jimmidyson/configmap-reload - watch a config map and sends an HTTP request after a change

## Storage  
https://github.com/signaleleven/s3fs-sidecar - mount an s3 bucket to a shared volume

## Git
https://github.com/kubernetes/git-sync - clones a git repo into a shared volume, keeps it in sync, and sends an HTTP request after a change
