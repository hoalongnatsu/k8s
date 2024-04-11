Run apply

```
kubectl apply -f hello-rs.yaml
```

List rs

```
kubectl get rs
```

List pod

```
kubectl get pod
```

Run port-forward

```
kubectl port-forward rs/hello-kube 3000:3000
```

Run delete

```
kubectl delete -f hello-rs.yaml
```