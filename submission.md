# Description de la remise

### Nom complet: XXXXX

### NIP: 111 111 111

### Liste des codes et descriptions des fonctionnalités sélectionnées:

Exemple:

-   (FA2) Intégration du Service Mesh Consul-Connect ==> 5%
-   (FA21) Intégration de la fonctionnalité de Service Discovery de Consul-Connect ==> 5%
-   (FA22) Observabilité des services et de leurs états (healthcheck) au travers du UI de Consul ==> 5%
-   (FA23) Définition d'Intentions limitant la communication entre les services au strict nécessaire ==> 10%
-   (FA24) Configuration de Canary Deployment et/ou Blue-green/A-B Deployment ==> 10%

### Directives nécessaires à la correction

-   il faut d'abord installer nginx avec helm pour que le service puisse être accessible
    ```bash
    helm upgrade --install ingress-nginx ingress-nginx \
        --repo https://kubernetes.github.io/ingress-nginx \
        --namespace ingress-nginx --create-namespace \
        --set controller.hostNetwork=true \
        --set controller.hostPort.enabled=true \
        --set controller.service.type=NodePort \
        --set dnsPolicy=ClusterFirstWithHostNet \
        --set controller.kind=DaemonSet
    ```
-   Pour la fonctionnalité additionnelle argocd, il faut créér un namespace argocd et installer argocd
    ```bash
    kubectl create namespace argocd
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    ```

### Commentaires généraux:

XXXXX
