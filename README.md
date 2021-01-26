# Istio playground

Personal playground for istio related stuff.

- Virtual service delegates:

```bash
kubectl create namespace delegate
kubectl label namespace delegate istio-injection=enabled

# Adapt your gateway host in gw.yml
kubectl apply -f ./delegate/gw.yml
kubectl apply -f ./delegate/a.yml
kubectl apply -f ./delegate/b.yml
kubectl apply -f ./delegate/dr.yml
kubectl apply -f ./delegate/vs-main.yml
kubectl apply -f ./delegate/vs-delegate-a.yml
kubectl apply -f ./delegate/vs-delegate-b.yml
```

Adapt your gateway host/port in the following URLs:

- http://test.delegate.org:32438/a/v1/ routes to service a, deployment v1
- http://test.delegate.org:32438/a/v2/ routes to service a, deployment v2
- http://test.delegate.org:32438/b/whatever/ routes to service b
- http://test.delegate.org:32438/a/not-managed/ routes to service a, 404 URL
