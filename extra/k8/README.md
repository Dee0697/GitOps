Pod-level settings:

restartPolicy:
nodeSelector:
tolerations:
affinity:
serviceAccountName:
volumes:
dnsPolicy:
hostNetwork:
initContainers:
securityContext (pod-level)
imagePullSecrets:


Container-level settings:

readiness behavior
liveness behavior
startup time
resource limits/requests
environment variables
ports
lifecycle logic (preStop/postStart)
VolumeMount

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


Examples (important) :

Object	        Controller watching it
Deployment       	Deployment controller
ReplicaSet	        ReplicaSet controller
Pod	Kubelet          (node-level controller)
Node	              Node controller
Job	                Job controller
CronJob         	CronJob controller
HPA	HPA              controller
PVC	CSI             external-provisioner
Ingress	            Ingress controller
Service	                kube-proxy
EndpointSlice       	EndpointSlice controller

📌 Even external components (CSI, CNI, Ingress) act as controllers.