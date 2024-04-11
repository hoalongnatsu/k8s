Build image

```
docker build . -t 080196/hello-kube
```

Push image

```
docker push 080196/hello-kube
```

Run apply

```
kubectl apply -f hello-kube.yaml
```

List pods

```
kubectl get pod
```

Run port-forward

```
kubectl port-forward pod/hello-kube 3000:3000
```

Run delete

```
kubectl delete -f hello-kube.yaml
```

List namespaces

```
kubectl get ns
```

Create a namespace

```
kubectl create ns testing
```

Run apply

```
kubectl apply -f hello-kube-ns.yaml
```

List pods in testing namespace

```
kubectl -n testing get pod
```

Run port-forward

```
kubectl -n testing port-forward pod/hello-kube 3000:3000
```