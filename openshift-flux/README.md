# Quickstart (OpenShift Flux)

1. **Install components with Flux.**

```sh
  oc login <openshift_url>
  oc project <project_name>

  oc apply -f ./openshift-flux
```

2. **Check Flux status.**

```sh
  oc get gitrepositories.source.toolkit.fluxcd.io 
  oc get kustomizations.kustomize.toolkit.fluxcd.io 
```

3. **Uninstall Bank of Anthos with Flux.**

```sh
  oc delete -f ./openshift-flux
```


# Links

- `https://fluxcd.io/`
- `https://kustomize.io/`