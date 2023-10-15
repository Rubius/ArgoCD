# ArgoCD

This repository contains ArgoCD Application, ApplicationSet, App of apps pattern examples

[Online Boutique](https://github.com/GoogleCloudPlatform/microservices-demo) microservices as a demo application used in the examples.

## Repo description

- [app-of-apps](./app-of-apps/) - folder where app-of-apps subapps Application manifests should be placed.
- [app-projects] - contains application manifests.
  - [online-boutique-demo-app.yaml](./app-projects/online-boutique-demo-app.yaml) - ArgoCD Application resource defines how to deploy an application called "[online-boutique-demo]https://github.com/GoogleCloudPlatform/microservices-demo)" from a Git repository to a Kubernetes cluster, following GitOps principles. It specifies the source repository, target cluster, sync policies, and metadata labels and annotations for the associated namespace.
  - [app-of-apps-demo.yaml](./app-projects/app-of-apps-demo.yaml) - ArgoCD Application resource defines how to implement app-of-apps pattern.
  - [application-set-demo.yaml](./app-projects/application-set-demo.yaml) - ArgoCD ApplicationSet resource allows to define and manage multiple applications as a group using a single configuration.
- [application-set](./application-set/) - folder for applicationSets subapps manifests (helm or Kustomize) should be placed.
- [microservices-demo](./microservices-demo/) - [Online Boutique](https://github.com/GoogleCloudPlatform/microservices-demo) Kustomize manifests. Additionally [frontend ingress](./microservices-demo/kustomize/overlay/frontend-ingress.yaml) resource to the ogriginal Kustomize manifests added. Please fix `ingressClassName` and `host` fields to your k8s actual cluster values before manifest applying.
- [settings](./settings/) - contain additional files
  - [online-boutique-demo-project.yaml](./settings/online-boutique-demo-project.yaml) - provided YAML configuration describes an ArgoCD AppProject resource, configuration is quite permissive, allowing applications within the "online-boutique-demo-project" to deploy from any source repository, deploy to any namespace and server, and manage resources of any group and kind.
  - [kustomization.yaml] -provided YAML configuration describes a Kustomize resource.

## How to use

- Fork repository.
- Clone forked repository locally.
- Fix [frontend ingress](./microservices-demo/kustomize/overlay/frontend-ingress.yaml)  `ingressClassName` and `host` fields to your k8s actual claster values before manifest applying.
- Commit changes to the remote repository.
- Apply [online-boutique-demo-project.yaml](./settings/online-boutique-demo-project.yaml) to create `online-boutique-demo-project` AppProject inyour k8s cluster.
- Apply [online-boutique-demo-app.yaml](./app-projects/online-boutique-demo-app.yaml) to create [Online Boutique](https://github.com/GoogleCloudPlatform/microservices-demo) microservices in your k8s cluster.
