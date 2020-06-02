# docker-mailserver-k3s

A kubectl YAML to deploy a docker-mailserver on Kubernetes

This YAML use Kustomize to decline different <env> in overlays directory. Please tune your <env> directory, or create new one base on the common files in "base" directory. 

## Post-Installation

You can tune the prod or dev Kustomize Overlay with :
- docker-mailserver-config.yaml : All configuration files (DNS, DKim, Mail Accounts)
- docker-mailserver-ingress.yaml : Domain name used to join the mail server

Note : the dev configuration use a "ClusterIssuer" object letsencrypt-staging, you must keep this configuration.

https://cert-manager.io/docs/concepts/issuer/

## Installation

The namespace used for this deployment is "mailserver".

```bash
# <env> must match your environment overlay
git clone https://github.com/kyzdev/docker-mailserver-k3s.git
cd docker-mailserver.git
kubectl apply -k overlays/<env>
```
## Uninstallation

```bash
# <env> must match your environment overlay
kubectl delete -k overlays/<env>
```

## Credits

https://github.com/tomav/docker-mailserver/wiki/Using-in-Kubernetes