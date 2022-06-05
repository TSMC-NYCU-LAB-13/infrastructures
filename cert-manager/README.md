# cert-manager

<!-- 
## 注意事項

- cert-manager-istio-csr 要在安裝 istio 以前安裝
 -->

## Download

- jetstack

    ```sh
    cd cert-manager
    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    helm repo update
    helm pull --untar --version v1.8.0 jetstack/cert-manager
    helm pull --untar --version v0.4.2 jetstack/cert-manager-istio-csr
    ```

## Install

- jetstack/cert-manager

    ```sh
    cd cert-manager/cert-manager
    helm upgrade --create-namespace --install -n cert-manager cert-manager . -f my-values.yaml
    ```
<!-- 
- jetstack/cert-manager-istio-csr

    ```sh
    # https://github.com/istio/istio/pull/38845
    # 如果用 helm 裝 istio 就無解惹
    cd cert-manager/cert-manager
    kubectl create namespace istio-system
    # 產生自簽 ca 憑證
    kubectl apply -f ../manifest/istio.yml
    helm upgrade --create-namespace --install -n cert-manager cert-manager-istio-csr . -f my-values.yaml
    ```

  - 或是引入自己準備好的自簽 ca 憑證

    ```sh
    # Export our cert from the secret it's stored in, and base64 decode to get the PEM data.
    kubectl get -n istio-system secret istio-ca -ogo-template='{{index .data "tls.crt"}}' | base64 -d > ca.pem

    # Out of interest, we can check out what our CA looks like
    openssl x509 -in ca.pem -noout -text

    # Add our CA to a secret
    kubectl create secret generic -n cert-manager istio-root-ca --from-file=ca.pem=ca.pem
    ```
-->

## 使用方法

- 參考[官方文件](https://cert-manager.io/docs/configuration/acme/dns01/cloudflare/)建立 Cloudflare API Token
- 使用以下方法建立 secret 並建立 ClusterIssuer 和 Certificate 資源
  
    ```sh
    cd cert-manager/manifest
    export API_TOKEN=xxxxx
    kubectl create secret generic cloudflare-api-token-secret --from-literal="api-token=$API_TOKEN" -n cert-manager
    kubectl apply -Rf .
    ```
