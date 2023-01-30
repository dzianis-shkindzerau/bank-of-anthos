# Quickstart (OpenShift)

1. **Build Bank of Anthos images .**

```
oc apply -f ./openshift/apps-build.yaml ???
```

2. **Deploy Bank of Anthos to the cluster.**

```
oc apply -f ./openshift-extras/jwt/jwt-secret.yaml
oc apply -f ./openshift/config.yaml

oc describe  template crunchy-pgadmin4-oauth -n openshift
oc get template -n openshift crunchy-pgadmin4-oauth -o yaml | oc process -f - -p PGADMIN_USER=admin -p PGADMIN_PASSWORD=admin  | oc apply -f -
oc delete all,cm,secrets,pvc -l app=pgadmin4

oc apply -f ./openshift/accounts-db-v2.yaml
oc apply -f ./openshift/userservice.yaml
oc apply -f ./openshift/contacts.yaml
oc apply -f ./openshift/frontend.yaml
oc apply -f ./openshift/ledger-db-v2.yaml
oc apply -f ./openshift/ledger-writer.yaml
oc apply -f ./openshift/balance-reader.yaml
oc apply -f ./openshift/transaction-history.yaml

oc apply -f ./openshift/loadgenerator.yaml
```

3. **Access the web frontend in a browser** using the frontend's external IP.

```
oc get service frontend | awk '{print $4}'
```

Visit `https://EXTERNAL_IP` to access your instance of Bank of Anthos.

4. **Uninstall Bank of Anthos from the cluster.**

```
oc delete all,cm,secrets,pvc -l app.kubernetes.io/part-of=bank-of-anthos
```



# Links

1. **database migration**

- `https://rtfm.co.ua/en/kubernetes-running-sql-migrations-with-kubernetes-job-and-helm-hook/#Kubernetes_Job`
