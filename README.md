# Helm charts


# Install EFK

```
kubectl create namespace logging

helm install --name es-operator \ 
--namespace logging \
--set rbac.create=false \
--tiller-namespace tiller-world \
./elasticsearch-operator

kubectl get pods -n logging

helm install --name efk 
--namespace logging \
--tiller-namespace tiller-world \
./efk 
```

# Check

```
kubectl get pods -n logging

NAME                                                  READY     STATUS    RESTARTS   AGE
efk-kibana-86c599cb7c-8xx78                           1/1       Running   0          4m
es-client-efk-cluster-7db7cb7879-zcl7b                1/1       Running   0          4m
es-data-efk-cluster-default-0                         1/1       Running   0          4m
es-master-efk-cluster-default-0                       1/1       Running   0          4m
es-operator-elasticsearch-operator-5977ff7c98-rz28f   1/1       Running   0          6m
fluent-bit-4vpzs                                      1/1       Running   0          4m
fluent-bit-gz55v                                      1/1       Running   0          4m
fluent-bit-hm5p8                                      1/1       Running   0          4m
```

[As a blogger](https://akomljen.com) and DevOps consultant I work with Helm and Kubernetes, in general, a lot.
This is my collection of Helm charts that I'm using to do some daily work, or just for research.

To start, add the repo first:
```
helm repo add akomljen-charts https://raw.githubusercontent.com/komljen/helm-charts/master/charts/
```

## Official Charts Repository

Why not use official charts repo?

Well, if you tried to contribute to the official charts repo you probably know that you need to wait a few weeks or more to merge. There are a lot of opened pull requests and they require the huge amount of work. A lot of people are learning Helm while contributing, so maintainers need to guide them. That is slow and sometimes I cannot wait for changes to get merged.

From time to time, I will sync those charts to official charts repo to make them available at [KubeApps](https://kubeapps.com/).
