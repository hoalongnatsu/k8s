Build image

```
docker build . -t 080196/hello-kube:v1
```

Push image

```
docker push 080196/hello-kube
```

Run apply

```
kubectl apply -f hello-deploy.yaml
```

List deploy

```
kubectl get deploy
```

List rs

```
kubectl get rs
```

List pods

```
kubectl get pod
```

Run port-forward

```
kubectl port-forward deploy/hello-app 3000:3000
```

---
Change code

```
const http = require("http");

const server = http.createServer((req, res) => {
  res.end("Hello application v2\n")
});

server.listen(3000, () => {
  console.log("Server listen on port 3000")
})

```

Build image v2

```
docker build . -t 080196/hello-kube:v2
```

Update yaml file and apply

```
kubectl apply -f hello-deploy.yaml
```

Check status

```
kubectl rollout status deploy hello-app
```

---
Rollback

Update code

```
const http = require("http");

let requestCount = 0;

const server = http.createServer((req, res) => {
  if (++requestCount > 3) {
    res.writeHead(500); // set status code 500
    res.end("Application v3 have some internal error has occurred!\n");
    return;
  }

  res.end("Hello application v3\n");
});

server.listen(3000, () => {
  console.log("Server listen on port 3000")
})
```

Build image

```
docker build . -t 080196/hello-kube:v3
```

Update yaml file and apply

```
kubectl apply -f hello-deploy.yaml
```

Run curl and get an error. Rollout undo

```
kubectl rollout undo deployment hello-app
```