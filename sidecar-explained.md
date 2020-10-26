# SideCar

## Intro
The sidecar design pattern is based on the fact that a pod can contain more than one container. Containers in a pod share the same network, storage and can share process namespace - enabling the sidecar containers to provide additional capabilities to the application container. (see the examples sections)

## Pros
- Providing capabilities to the application without changing the code
- Separate resources and ownership, a sidecar is a different container and can have its own configuration (resources, health check...)
- In multiple languages environment, a sidecar can replace the need to publish multiple libraries (One for each language)

## Cons
- Sidecar is not a first class object in k8s; thus, there is no way to easily control the sidecar's lifecycle related to the application container. For example, there isn't a declarative way to state that a container is a sidecar and should start before the application container and shut down after it
- Sidecar containers impact the HPA and the VPA
- Sidecar containers can fail (like any other code), causing problems in your application (for example if the proxy sidecar fails, you won't have any network)

## Sharing Resources Examples
### Network


### Storage
```
apiVersion: v1
kind: Pod
metadata:
  name: storage sharing
spec:
  volumes:
    - name: shared-logs
      emptyDir: {}

  containers:
    - name: app
      image: busybox
      command: ["sh","-c","while true; do echo hello from the application >> /var/log/log.txt; sleep 30; done]
      volumeMounts:
        - name: shared-logs
          mountPath: /var/log

    - name: sidecar
      image: busybox
      command: ["sh","-c","while true; do cat /var/log/nginx/log.txt; sleep 30; done"]
      volumeMounts:
        - name: shared-logs
          mountPath: /var/log/nginx
```
### PID namespace
see full explanation: https://kubernetes.io/docs/tasks/configure-pod-container/share-process-namespace/
