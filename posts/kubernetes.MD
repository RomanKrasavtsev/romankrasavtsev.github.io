# Secrets
```
kubectl get secret comonea-product-adapter \
   -n $NAMESPACE \
   -o jsonpath --template '{.data.$KEY}' | base64 -D
```
