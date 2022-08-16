# flux-issues
Demonstrate issues with flux

Each example has an install file available that will install set up a flux
kustomization resource to demonstrate the problem.

Just run `kubectl apply -f install.yaml` to set things up.

# SOPS

The main issue with SOPS is that the kustomize controller first runs kustomize,
and then runs SOPS. This means that the various SOPS pieces are merged into a
single file that SOPS cannot decrypt.

There is a GPG key in the `sops` directory that can be used to decrypt the
examples.

You can run this to add the GPG key to your cluster:

```
kubectl create secret generic sops-gpg \
--namespace=flux-system \
--from-file=sops/sops.asc
```
