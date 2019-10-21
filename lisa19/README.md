# This directory is supplemental things to help setup the environment for LISA 19

# Add the repo
argocd repo add https://github.com/cooktheryan/federation-dev.git

# Add clusters
argocd cluster add east1
argocd cluster add east2
argocd cluster add west2

# Define simple app
argocd app create --project default --name simple-app \
--repo https://github.com/cooktheryan/federation-dev.git \
--path lisa19/simple-app \
--dest-server east1 \
--dest-namespace simple-app  \
--revision master \
--sync-policy automated
