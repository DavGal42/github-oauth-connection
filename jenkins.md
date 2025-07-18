# Jenkins Connection
### How Connect to Jenkins UI using Github OAuth App in local environment.
---

### 1. Create GitHub OAuth App
- Homepage URL

  ```http://localhost:8080```

- Authorization Callback URL

  ```http://localhost:8080/api/dex/callback```

### 2. Install ArgoCD
[Here's the link](https://www.jenkins.io/doc/book/installing/)

### 3. Download Github Authentication Plugin
Go to
```Manage Jenkins → Plugins → Available Plugins → Github Authentication Plugin```

### 4. Configure Github Authentication Plugin
Go to ```Manage Jenkins → Security → Security Realm → Github Authentication Plugin```

### 5. Configure users permissions
Go to ```Manage Jenkins → Security → Authorization```
