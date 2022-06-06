# storage

## Download

- rook-release

    ```sh
    cd storage
    helm repo add rook-release https://charts.rook.io/release
    helm repo update
    helm pull --untar --version v1.9.4 rook-release/rook-ceph
    helm pull --untar --version v1.9.4 rook-release/rook-ceph-cluster
    ```

## Install

- rook-release/rook-ceph

    ```sh
    cd storage/rook-ceph
    helm upgrade --create-namespace --install -n rook-ceph rook-ceph . -f my-values.yaml
    ```

- rook-release/rook-ceph-cluster

    ```sh
    cd storage/rook-ceph-cluster
    helm upgrade --create-namespace --install -n rook-ceph rook-ceph-cluster . -f my-values.yaml
    ```
