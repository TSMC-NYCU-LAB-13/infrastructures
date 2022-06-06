# database

## Download

- bitnami

    ```sh
    cd queue
    helm repo add bitnami https://charts.bitnami.com/bitnami
    helm repo update
    helm pull --untar --version 10.1.4 bitnami/rabbitmq
    ```

## Install

- bitnami/rabbitmq

    ```sh
    cd queue/rabbitmq
    helm upgrade --create-namespace --install -n rabbitmq rabbitmq . -f my-values.yaml
    ```
