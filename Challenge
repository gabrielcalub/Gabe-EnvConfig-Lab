## Step 1: Create the Production Namespace

```bash
kubectl create namespace production
```

## Step 2: Create a ConfigMap for Application Configuration

```bash
kubectl create configmap app-config \
  --from-literal=APP_ENV=production \
  --namespace=production
```

## Step 3: Create a Secret for Sensitive Information

```bash
kubectl create secret generic app-secret \
  --from-literal=DB_PASSWORD=prodpassword123 \
  --namespace=production
```

## Step 4: List Created Secrets

```bash
kubectl get secrets -n production
```

---

## Step 5: Modify the Deployment Template for Production

```bash
sed -e 's/PLACEHOLDER_NAMESPACE/production/' \
    -e 's/replicas: .*$/replicas: 3/' app-deployment-template.yaml > production-deployment.yaml
```

## Step 6: Apply the Deployment Configuration

```bash
kubectl apply -f production-deployment.yaml
```

---

## Step 7: Expose the Application as a Service

```bash
kubectl expose deployment nginx-app \
    --type=NodePort \
    --name=nginx-service \
    --port=80 \
    --target-port=80 \
    --namespace=production
```

## Step 8: Verify the Deployment and Service

```bash
kubectl get pods -n production
kubectl get service -n production
```

---

## Step 9: Execute into a Running Pod

```bash
kubectl exec -it nginx-app-65968468b6-8c59n -n production -- /bin/bash
```

### Verify Environment Variables

```bash
echo $APP_ENV
echo $DB_PASSWORD
```
