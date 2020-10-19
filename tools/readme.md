# Migrate assets of Azure Dev Spaces to Bridge to Kubernetes
This directory contains a script to deploy resources/assets that used to be deployed by Azure Dev Spaces.

## Overview
This tool will re-deploy your resources using the assets generated by Azure Dev Spaces. Specifically, it does following steps:
1. Builds the docker file and pushes the image to container registry.
2. Deploys the helm charts.
3. If required, deploys an ingress controller to provide a public endpoint to access the service over the internet.

## Prerequisites
Please install the below pre-requisites if using this on your local machine, or alternately, you can just use azure bash [cloudshell](https://shell.azure.com/ ) for a seamless experience.
1. [azure cli](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
2. [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
3. [docker](https://docs.docker.com/engine/install/)
4. curl
5. gunzip
6. tar

## Use the tool
```
migrate-devspaces-assets.sh -g ResourceGroupName -n AKSName -h ContainerRegistryName  
Flags:  
    -g Name of resource group of AKS Cluster [required]
    -n Name of AKS Cluster [required]
    -h Container registry name. Examples: ACR, Docker [required]
    -k Kubernetes namespace to deploy resources (uses 'default' otherwise)
    -r Path to root of the project that needs to be migrated (default = pwd)
    -t Image name & tag in format 'name:tag' (default = 'projectName:stable')
    -i Enable a public endpoint to access your service over internet. (default = false)
    -y Doesn't prompt for non-tty terminals
    -d Helm Debug switch  
```