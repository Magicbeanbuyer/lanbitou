#k8s 

![](https://media.licdn.com/dms/image/C5112AQHhEb_mvm_qXg/article-cover_image-shrink_600_2000/0/1580818857721?e=1684972800&v=beta&t=Tqgtc7HYsUnkrBUNRhcYLPy3r0BlifVx9TVArNOVNos)

ConfigMap data can be consumed in Pod broadly either as an environment variable or by mounting them as files in a container.

In Kubernetes, ConfigMaps and [[Secret]]s are two objects using which configuration data can be passed to [[Pod]]s and containers running within them.

It stores the data as key-value pairs, where value can be a string or entire content of a file.

`kubectl create configmap`

Kubernetes do not put any hard limits on ConfigMap size, though it stores configMaps in [[etcd]]. Etcd has hard limit to store value up to 1MB