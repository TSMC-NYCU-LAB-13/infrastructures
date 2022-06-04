# network

## Download

- istio

    ```sh
    cd network/istio
    helm repo add istio https://istio-release.storage.googleapis.com/charts
    helm repo update
    helm pull --untar --version 1.13.4 istio/base
    helm pull --untar --version 1.13.4 istio/istiod
    helm pull --untar --version 1.13.4 istio/gateway
    ```
<!-- 
- kiali

    ```sh
    cd network/kiali-operator
    helm repo add kiali https://kiali.org/helm-charts
    helm repo update
    helm pull --untar --version 1.51.0 kiali/kiali-operator
    ``` 
-->

## Install

- istio/base

    ```sh
    cd network/istio/base
    helm upgrade --create-namespace --install -n istio-system istio-base . -f my-values.yaml
    ```

- istio/istiod

    ```sh
    cd network/istio/istiod
    helm upgrade --create-namespace --install -n istio-system istiod . -f my-values.yaml
    ```

- istio/gateway

    ```sh
    cd network/istio/gateway
    helm upgrade --create-namespace --install -n istio-system istio-ingress . -f my-values.yaml
    ```

<!-- 
- kiali/kiali-operator

    ```sh
    cd network/istio/kiali-operator
    helm upgrade --create-namespace --install -n istio-system kiali-operator . -f my-values.yaml
    ``` 
-->
