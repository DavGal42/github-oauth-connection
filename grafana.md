### How Connect to Grafana UI using Github OAuth App in local environment.

---

<img width="1000" height="500" alt="Screenshot from 2025-07-21 19-21-16" src="https://github.com/user-attachments/assets/74a6e436-5345-4f19-8586-d435597871ee" />
<p align="center">
  <img width="300" height="600" alt="Screenshot from 2025-07-21 19-21-49" src="https://github.com/user-attachments/assets/c0bab72c-4329-4164-97d5-a73127af8523" />
</p>
<img width="1000" height="300" alt="Screenshot from 2025-07-21 19-22-28" src="https://github.com/user-attachments/assets/b4c40da5-685e-44fa-967d-9fbc91e005ee" />

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
