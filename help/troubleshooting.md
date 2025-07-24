---
title: Résolution des problèmes liés aux formulaires adaptatifs découplés
description: Résolution des problèmes liés aux formulaires adaptatifs découplés
keywords: découplé, formulaire adaptatif, dépannage
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 58%

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
