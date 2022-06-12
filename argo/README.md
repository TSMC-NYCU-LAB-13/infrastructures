# argo

## Download

- argo

    ```sh
    cd argo
    helm repo add argo https://argoproj.github.io/argo-helm
    helm repo update
    helm pull --untar --version 4.8.0 argo/argo-cd
    helm pull --untar --version 2.16.0 argo/argo-rollouts
    helm pull --untar --version 0.8.0 argo/argocd-image-updater
    ```

## Install

- argo/argo-cd

    ```sh
    cd argo/argo-cd
    helm upgrade --create-namespace --install -n argocd argocd . -f my-values.yaml
    ```

- argo/argo-rollouts

    ```sh
    cd argo/argo-rollouts
    helm upgrade --create-namespace --install -n argocd argo-rollouts . -f my-values.yaml
    ```

- argo/argo-rollouts

    ```sh
    cd argo/argocd-image-updater
    helm upgrade --create-namespace --install -n argocd argocd-image-updater . -f my-values.yaml
    ```
