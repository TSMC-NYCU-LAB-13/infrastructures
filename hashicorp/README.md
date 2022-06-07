# hashicorp

## Download

- hashicorp

    ```sh
    cd hashicorp
    helm repo add hashicorp https://helm.releases.hashicorp.com
    helm repo update
    helm pull --untar --version 0.20.1 hashicorp/vault
    ```

## Install

- hashicorp/vault

    ```sh
    cd hashicorp/vault
    helm upgrade --create-namespace --install -n vault vault . -f my-values.yaml

    # 第 0 個 vault
    kubectl exec -n vault -ti vault-0 -- vault operator init
    kubectl exec -n vault -ti vault-0 -- vault operator unseal

    # 其他的 vault <舉例第 1 個>
    kubectl exec -n vault -ti vault-1 -- vault operator unseal
    ```
