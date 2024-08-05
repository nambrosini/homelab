# Homelab setup

1. Deploy argocd using helm
```bash
helm install argocd --values charts/argocd/values.yaml charts/argocd
```
2. Deploy tailscale using argocd

## Tailscale
Create the following secret in tailscale 
```yaml
apiVersion: v1
data:
  client_id: <CLIENT_ID>
  client_secret: <CLIENT_SECRET>
kind: Secret
metadata:
  labels:
    app.kubernetes.io/managed-by: Helm
  name: operator-oauth
  namespace: tailscale-system
type: Opaque
```
[Create Tailscale OAuth client](https://tailscale.com/kb/1215/oauth-clients#setting-up-an-oauth-client)
