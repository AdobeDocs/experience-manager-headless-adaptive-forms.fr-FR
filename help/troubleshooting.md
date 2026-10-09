---
title: Résolution des problèmes liés aux formulaires adaptatifs découplés
description: Résolution des problèmes liés aux formulaires adaptatifs découplés
keywords: découplé, formulaire adaptatif, dépannage
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
index: true
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
TQID: 'https://experienceleague.adobe.com/yjO3VhNmqIAyfnD7daHB7eAEUNmaAjnUgEm0fHc1ArY'
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: b34afbc4f692b81838ad6947895c9b347dff6d62
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 65%
---
# Résolution des problèmes

## Impossible de déployer le projet d’archétype dans un environnement de développement local

### Problème

Lorsque vous utilisez la `mvn -PautoInstallPackage clean install` ou des commandes similaires pour déployer un projet de l’archétype AEM, le déploiement du projet échoue.

### Raison

Cela peut se produire en raison d&#39;une version non prise en charge ou d&#39;une installation corrompue de `node.js` ou `NPM`.

### Solution

1. [Supprimez complètement les installations existantes de Node.JS](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) de votre environnement.

1. Installez `node.JS 16.13.0` ou une version ultérieure avec `NPM`.

1. Redémarrez votre machine.


## Impossible d’exécuter la commande `mvn clean install`.

### Problème

Lorsque vous utilisez la commande `mvn clean install` ou des commandes similaires pour déployer un projet AEM Archetype, l’exécution de la commande échoue.

### Raison

Ce problème peut se produire si Git n’est pas installé.

### Solution

Téléchargez et installez la [dernière version de Git](https://git-scm.com/downloads). Si vous découvrez Git, consultez [Installer Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
