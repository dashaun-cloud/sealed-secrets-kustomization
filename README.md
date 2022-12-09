# Sealed Secrets Kustomization

For use with [FluxCD](https://fluxcd.io) to deploy [bitnami-labs/sealed-secrets](https://github.com/bitnami-labs/sealed-secrets)

## Add the GitRepository

```bash
flux create source git sealed-secrets \
  --url=https://github.com/dashaun-cloud/sealed-secrets-kustomization \
  --branch=main \
  --interval=1m \
  --export > ./clusters/cluster00/sealed-secrets-kustomization-source.yaml
```

## Add the Kustomization

```bash
flux create kustomization sealed-secrets \
  --source=sealed-secrets \
  --path="./kustomize" \
  --prune=true \
  --interval=3m \
  --export > ./clusters/cluster00/sealed-secrets-kustomization.yaml
```