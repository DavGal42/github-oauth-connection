# ArgoCD Connection
### How Connect to ArgoCD UI using Github OAuth App in local environment.
---

### 1. Create GitHub OAuth App
- Homepage URL

  ```http://localhost:8080```

- Authorization Callback URL

  ```http://localhost:8080/api/dex/callback```

### 2. Install ArgoCD
[Here's the link](https://argo-cd.readthedocs.io/en/stable/getting_started/)

### 3. Turn off HTTPS for ArgoCD
```
kubectl -n argocd patch deployment argocd-server \
  --type=json \
  -p='[{"op":"add","path":"/spec/template/spec/containers/0/args","value":["argocd-server","--insecure"]}]'
```

### 4. Edit argocd-cm
```kubectl edit cm argocd-cm -n argocd```

```
apiVersion: v1
kind: ConfigMap
metadata:
  name: argocd-cm
  namespace: argocd
data:
  url: http://localhost:8080
  dex.config: |
    connectors:
    - type: github
      id: github
      name: GitHub
      config:
        clientID: <YOUR_CLIENT_ID>
        clientSecret: $dex.github.clientSecret
```

### 5. Edit argocd-secret
```kubectl edit secret argocd-secret -n argocd```

```
apiVersion: v1
kind: Secret
metadata:
  name: argocd-secret
  namespace: argocd
type: Opaque
stringData:
  dex.github.clientSecret: <YOUR_CLIENT_SECRET>
```

### 6. Restart ArgoCD deployment
```kubectl -n argocd rollout restart deployment argocd-server```
