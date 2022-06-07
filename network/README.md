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

- oauth2-proxy

    ```sh
    cd network
    helm repo add oauth2-proxy https://oauth2-proxy.github.io/manifests
    helm repo update
    helm pull --untar --version 6.2.1 oauth2-proxy/oauth2-proxy
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

- oauth2-proxy/oauth2-proxy

    ```sh
    cd network/oauth2-proxy
    helm upgrade --create-namespace --install -n oauth2-proxy oauth2-proxy . -f my-values.yaml
    ```

<!-- 
- kiali/kiali-operator

    ```sh
    cd network/istio/kiali-operator
    helm upgrade --create-namespace --install -n istio-system kiali-operator . -f my-values.yaml
    ``` 
-->
