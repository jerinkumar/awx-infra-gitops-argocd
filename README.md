This project is mainly focussed on setting up an AWX environment with Postgres as the backend database.

This will be run at the DR site.

Day-1 setup

1. Clone the github repository -
     git clone https://github.com/jerinkumar/awx-infra-gitops-argocd.git
     cd awx-infra-gitops-argocd
2. Install Metallb by executing -
    # 1️⃣ Make sure the subfolders exist
    mkdir -p metallb/manifests
    # 2️⃣ Then download the manifest properly
    curl -L -o metallb/manifests/metallb-native.yaml \
    https://raw.githubusercontent.com/metallb/metallb/v0.14.5/config/manifests/metallb-native.yaml
    kubectl apply -k ./metallb
3. Install ArgoCD by executing -
   cd awx-infra-gitops-argocd/argocd/base
   curl -L -o install.yaml https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   kubectl apply -k ./argocd
