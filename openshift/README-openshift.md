# Quickstart (OpenShift)

1. **Clone Bank of Anthos repository .**

```
git clone https://github.com/dzianis-shkindzerau/bank-of-anthos.git
cd bank-of-anthos/
```

2. **Deploy Bank of Anthos to the OpenShift cluster.**

```
oc login <openshift_url>
oc project <project_name>

oc apply -f ./openshift/configs
oc apply -f ./openshift
oc get template -n openshift crunchy-pgadmin4-oauth -o yaml | oc process -f - -p PGADMIN_USER=admin -p PGADMIN_PASSWORD=admin  | oc apply -f -
```

3. **Access the web frontend in a browser** using the frontend's external IP.

```
oc get route frontend | awk '{print $2}'
```

Visit `https://HOST` to access your instance of Bank of Anthos.

4. **Uninstall Bank of Anthos from the cluster.**

```
oc delete all,cm,sa,secrets,pvc -l app=pgadmin4 
oc delete all,cm,sa,secrets,pvc,PostgresCluster -l app.kubernetes.io/part-of=bank-of-anthos
```



# Links

1. **database migration**

- `https://rtfm.co.ua/en/kubernetes-running-sql-migrations-with-kubernetes-job-and-helm-hook/#Kubernetes_Job`
