# Maya GitOps

> **O8 status — 2026-10-01:** `KEEP / PRODUCT_OWNED_GITOPS / NOT_IMPLEMENTED`.
>
> Ce dépôt est conservé parce que `zdmooc/Maya` le référence explicitement comme propriétaire du déploiement Maya. Il ne possède ni l'installation Argo CD/OpenShift GitOps, ni les services techniques communs.
Dépôt GitOps de la plateforme **Maya** de Maya Interlink Solutions.

Ce dépôt contient uniquement la configuration de déploiement et d’exploitation OpenShift. Le code applicatif, l’IA et les livrables d’architecture restent dans `zdmooc/Maya`.

## Première cible

**OpenShift Local / CRC** sur HP ZBook 17 G3.

## Structure cible

```text
Maya-gitops/
├── base/
│   ├── maya-api/
│   ├── maya-architect/
│   ├── maya-trading/
│   ├── maya-rag/
│   ├── postgres/
│   ├── qdrant/
│   └── observability/
├── environments/
│   ├── crc/
│   ├── dev/
│   ├── preprod/
│   └── prod/
├── argocd/
│   ├── applications/
│   └── applicationsets/
├── policies/
└── README.md
```

## Principe de déploiement initial

Le LLM local pourra d’abord être exécuté hors CRC (Windows/WSL2/Ollama) afin de limiter la consommation mémoire et de simplifier l’accès GPU. Les services Maya déployés dans OpenShift l’appelleront par API.

## Règles

- Git est la source de vérité pour les manifests.
- Aucun secret en clair dans Git.
- Chaque environnement possède sa configuration propre.
- CRC sert de laboratoire et de plateforme de benchmark avant migration vers le futur poste de travail.

## Frontières de responsabilité O8

```text
argocd-expert-pack
  Argo CD / OpenShift GitOps specialist patterns and operations
        |
        v
Maya-gitops
  Maya-specific desired state / overlays / Applications
        |
        v
Maya product workloads

shared-platform-services-openshift
  shared IAM / observability / quality / secrets contracts
```

Le dépôt doit **consommer** les patterns Argo CD et les contrats de plateforme ; il ne doit pas copier Keycloak, SonarQube, observabilité, PKI ou une installation Argo CD complète.

## Niveau de preuve actuel

- structure cible documentée : `REFERENCE` ;
- manifests Maya exécutables : `NOT_IMPLEMENTED` ;
- Argo CD Application Synced/Healthy : `NOT_PROVEN` ;
- CRC/OpenShift Maya : `NOT_PROVEN` ;
- production : `NOT_CLAIMED`.

La présence de ce README ne constitue pas une preuve de déploiement.
