# Ingress

General ingress file looks something like this. We will consider this as `ingress.yml`

```yml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  ingressClassName: example-ingress
  defaultBackend:
    service:
      name: ng-service
      port:
        number: 3000
  rules:
  - host: hello.test
    http:
      paths:
      - path: /ng
        pathType: Prefix
        backend:
          service:
            name: ng-service
            port:
              number: 80
      - path: /wmd
        pathType: Prefix
        backend:
          service:
            name: wmd-service
            port:
              number: 3000
```