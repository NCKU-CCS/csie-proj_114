## Helm 裝 Postgres 我的作法

1. 在本地端裝postgres
    
    ```Shell
    helm install ymh-postgresql-0 bitnami/postgresql --namespace ymh-webapp --set global.postgresql.auth.postgresPassword=postgresmaster --set global.postgresql.auth.password=postgresmaster --set global.postgresql.auth.username=postgres --set global.postgresql.auth.database=test
    ```
    
    下面這兩個指令是要試連用的
    ```Shell
    export POSTGRES_PASSWORD=$(kubectl get secret --namespace ymh-webapp ymh-postgres-postgresql -o jsonpath="{.data.postgres-password}" | base64 -d)
    ```

    ```Shell
    kubectl run ymh-postgres-postgresql-client --rm --tty -i --restart='Never' --namespace ymh-webapp --image docker.io/bitnami/postgresql:16.1.0-debian-11-r9 --env="PGPASSWORD=$POSTGRES_PASSWORD" \
      --command -- psql --host ymh-postgres-postgresql -U postgres -d test -p 5432
    ```

2. 把本地端的檔案導出

    ```Shell
    helm get values <release-name> > values.yaml
    ```

3. 確認檔案是對的、並且接上遠端的kubeconfig，然後刪除本地端的

    ```Shell
    export KUBECONFIG=/Users/huangyoumei/poetry-demo/kubeconfig.yaml
    helm uninstall <release-name>
    ```
4. 部署到遠端

    ```Shell
    helm install <release-name> -f values.yaml <chart-name>
    ```

    