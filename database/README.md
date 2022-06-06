# database

## Download

- bitnami

    ```sh
    cd database
    helm repo add bitnami https://charts.bitnami.com/bitnami
    helm repo update
    helm pull --untar --version 7.3.2 bitnami/mariadb-galera
    ```

## Install

- bitnami/mariadb-galera

    ```sh
    cd database/mariadb-galera
    helm upgrade --create-namespace --install -n mariadb-galera mariadb-galera . -f my-values.yaml
    ```
