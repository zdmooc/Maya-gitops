# Maya GitOps

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
