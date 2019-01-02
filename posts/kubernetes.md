# Deployments

## get
```
kubectl get deployments -n $NAMESPACE
```

## scale
```
kubectl scale -n $NAMESPACE --replicas=$AMOUNT deployment/$DEPLOYMENT
```

# Logs

```
kubectl logs -n $NAMESPACE $POD
```

# Secrets

## get
```
kubectl get secret $SECRET \
   -n $NAMESPACE \
   -o jsonpath --template '{.data.$KEY}' | base64 -D
```
