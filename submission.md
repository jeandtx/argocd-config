# Description de la remise

### Nom complet: Doutriaux Jean

### NIP: 537 316 169

### Nom complet: Pontus

### NIP: 111 111 111

### Liste des codes et descriptions des fonctionnalités sélectionnées:

-   (FA1) Sécuriser et encrypter les communications au travers de certificats SSL. ==> 10%
-   (FA41) Intégration d’un système de Continuous Delivery (ArgoCD, ...) ==> 15%

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
    Ensuite pour vérifier le statut de argocd on peut utiliser la commande suivante, de sorte à récuperer le dashboard sur https://localhost:8081
    ```bash
    kubectl port-forward -n argocd svc/argocd-server 8081:80
    ```
    le mot de passe par défault s'obtient avec la commande suivante
    ```bash
    k get secret argocd-initial-admin-secret -n argocd -o yaml
    ```
-   Un fichier yaml est en dehors du dossier submission car il doit être situé à la racine du projet (argocd)

### Commentaires généraux:
