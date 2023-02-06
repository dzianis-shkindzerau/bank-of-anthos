# Quickstart (OpenShift Flux)

1. **Install Flux resources.**

```sh
  oc login <openshift_url>
  oc project <project_name>

  oc apply -k ./openshift-flux
```

2. **Check status.**

```sh
  oc get gitrepositories.source.toolkit.fluxcd.io 
  oc get kustomizations.kustomize.toolkit.fluxcd.io 
  oc get kustomizations.kustomize.config.k8s.io
```


# Links

- `https://fluxcd.io/flux/`