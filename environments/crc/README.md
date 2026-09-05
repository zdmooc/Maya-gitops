# Environnement CRC

Environnement de laboratoire OpenShift Local utilisé pour le prototype Maya sur le HP ZBook 17 G3.

## Objectifs

- valider le déploiement des services Maya sur OpenShift ;
- mesurer la consommation CPU/RAM/stockage ;
- tester GitOps et Argo CD ;
- identifier les limites du ZBook avant achat du futur portable cible.

## Baseline ZBook

- CPU : Intel Core i7-6820HQ, 4 cœurs / 8 threads
- RAM : 64 Go
- GPU : NVIDIA Quadro M3000M
- VRAM : 4 Go
- SSD : environ 1 To
- OS : Windows 11 Pro

## Principe V1

Dans les premières itérations, le LLM local est exécuté hors du cluster CRC via Ollama/llama.cpp sur l’hôte. Les workloads OpenShift communiquent avec le moteur IA par API.

Cette séparation permet de mesurer indépendamment :

1. la charge OpenShift ;
2. la charge du modèle IA ;
3. la charge combinée de Maya Architect et Maya Trading.
