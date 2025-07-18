# Grafana Connection

### How Connect to Grafana UI using Github OAuth App in local environment.

---

### 1. Create GitHub OAuth App
Homepage URL

```http://localhost:3000```

Authorization Callback URL

```http://localhost:3000/login/github```

### 2. Install Grafana
[Here's the link](https://grafana.com/docs/grafana/latest/setup-grafana/installation/)

### 3. Edit grafana.ini   
```ini
[auth.github]
enabled = true
allow_sign_up = true
client_id = <CLIENT_ID>
client_secret = <CLIENT_SECRET>
scopes = user:email,read:org
auth_url = https://github.com/login/oauth/authorize
token_url = https://github.com/login/oauth/access_token
api_url = https://api.github.com/user
allowed_organizations = <your-org-name>
```

### 4. Restart Grafana service
```sudo systemctl restart grafana-server```
