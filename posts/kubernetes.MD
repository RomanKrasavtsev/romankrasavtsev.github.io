# Secrets

## get
```
kubectl get secret comonea-product-adapter \
   -n $NAMESPACE \
   -o jsonpath --template '{.data.$KEY}' | base64 -D
```

# Deployments

## get
```
kubectl get deployments -n $NAMESPACE
```

## scale
```
kubectl scale -n $NAMESPACE --replicas=$AMOUNT deployment/$DEPLOYMENT
```
