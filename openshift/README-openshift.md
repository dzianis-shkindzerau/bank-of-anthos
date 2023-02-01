# Quickstart (OpenShift)

1. **Build Bank of Anthos images .**

```
git clone https://github.com/GoogleCloudPlatform/bank-of-anthos.git
cd bank-of-anthos/
```

2. **Deploy Bank of Anthos to the cluster.**

```
oc apply -f ./openshift/configs
oc apply -f ./openshift
oc get template -n openshift crunchy-pgadmin4-oauth -o yaml | oc process -f - -p PGADMIN_USER=admin -p PGADMIN_PASSWORD=admin  | oc apply -f -
```

3. **Access the web frontend in a browser** using the frontend's external IP.

```
oc get service frontend | awk '{print $4}'
```

Visit `https://EXTERNAL_IP` to access your instance of Bank of Anthos.

4. **Uninstall Bank of Anthos from the cluster.**

```
oc delete all,cm,sa,secrets,pvc -l app=pgadmin4 
oc delete all,cm,sa,secrets,pvc,PostgresCluster -l app.kubernetes.io/part-of=bank-of-anthos
```



# Links

1. **database migration**

- `https://rtfm.co.ua/en/kubernetes-running-sql-migrations-with-kubernetes-job-and-helm-hook/#Kubernetes_Job`
