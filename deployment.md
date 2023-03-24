#k8s 

One step higher in the abstraction hierarchy, deployments control both [[ReplicaSet]]s and [[pod]]s in a declarative manner. 

This means that you define what you want your collection of pods to be, and the deployment makes use of several other Kubernetes objects to ensure that things are as you’ve declared in your YAML file.

The declarative definitions for Kubernetes Deployments live in [[etcd]].

This is different than a ReplicaSet in that you can roll out changes to the desired state of the system by changing the pod template in your deployment YAML, and the deployment will take care of the rest. You can also revert to a previous state if things go awry. This contrasts with a ReplicaSet in that if you were to change the ReplicaSet’s YAML and then run `<kubectl apply -f <replicaset.yml>` your original ReplicaSet will persist. And with that, you’ll be creating a second ReplicaSet. `</replicaset.yml>`