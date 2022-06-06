# monitoring

## Download

- prometheus-community

    ```sh
    cd monitoring/prometheus
    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    helm repo update
    helm pull --untar --version 35.5.1 prometheus-community/kube-prometheus-stack
    ```

- jaegertracing

    ```sh
    cd monitoring/tracing
    helm repo add jaegertracing https://jaegertracing.github.io/helm-charts
    helm repo update
    helm pull --untar --version 0.56.5 jaegertracing/jaeger
    ```

- kiali

    ```sh
    cd monitoring
    helm repo add kiali https://kiali.org/helm-charts
    helm repo update
    helm pull --untar --version 1.51.0 kiali/kiali-operator
    ```

- grafana/loki-stack

    ```sh
    cd monitoring
    helm repo add grafana https://grafana.github.io/helm-charts
    helm repo update
    helm pull --untar --version 2.6.4 grafana/loki-stack
    ```

## Install

- prometheus-community/kube-prometheus-stack

    ```sh
    cd monitoring/prometheus/kube-prometheus-stack
    helm upgrade --create-namespace --install -n monitoring kube-prometheus-stack . -f my-values.yaml
    ```

- jaegertracing/jaeger

    ```sh
    cd monitoring/tracing/jaeger
    # ENV ISSUE
    # https://github.com/grafana/loki/issues/480
    # https://github.com/kiali/kiali/blob/7408e707b2c876d13694cbb02d7b9104fd6b9952/jaeger/client.go#L259
    helm upgrade --create-namespace --install -n monitoring jaeger-tracing . -f my-values.yaml
    ```

- kiali/kiali-operator

    ```sh
    cd monitoring/kiali-operator
    helm upgrade --create-namespace --install -n monitoring kiali-operator . -f my-values.yaml
    ```

- grafana/loki-stack

    ```sh
    cd monitoring/loki-stack
    helm upgrade --create-namespace --install -n monitoring loki-stack . -f my-values.yaml
    ```
