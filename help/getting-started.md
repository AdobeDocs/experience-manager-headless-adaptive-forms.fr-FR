---
title: Prise en main des formulaires adaptatifs découplés
description: Prise en main des formulaires adaptatifs découplés
keywords: découplé, formulaire adaptatif, tutoriel
hide: true
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 50%

---


# Prise en main du Forms adaptatif découplé

Ce tutoriel vous fournit un cadre de bout en bout pour créer un formulaire adaptatif découplé. Le tutoriel consiste en un cas d’utilisation et plusieurs guides. Chaque guide décrit des fonctionnalités spécifiques et vous aide à les ajouter au formulaire adaptatif découplé créé dans ce tutoriel. Chaque guide se termine par un formulaire adaptatif découplé opérationnel. À la fin de ce tutoriel, vous devriez pouvoir effectuer les opérations suivantes :

* créer un formulaire adaptatif découplé ;
* ajouter des règles commerciales à votre formulaire ;
* utiliser Material UI de Google pour appliquer un style au formulaire ;
* Préremplir le formulaire
* incorporer le formulaire dans une page web.

Vous allez également acquérir une compréhension de l’architecture, des artefacts disponibles et de la structure JSON des formulaires adaptatifs découplés.

**Commençons par aborder un cas d’utilisation** :

Raya Tan, membre du Département des affaires étrangères d&#39;un pays connu pour sa beauté naturelle et son économie touristique florissante, supervise la distribution des formulaires de visa aux touristes. Ces formulaires sont disponibles sur le site web du ministère, les applications mobiles natives et au format PDF, et ce dans plusieurs langues. Cependant, la gestion et la distribution de ces formulaires sur différentes plateformes et technologies peut s’avérer difficile.

Afin d’améliorer l’efficacité et la flexibilité de son processus de demande de visa, le Département des affaires étrangères a décidé d’adopter une approche basée sur les formulaires adaptatifs découplés. Cette architecture découplée sépare le front-end du back-end, pour davantage de personnalisation et d’évolutivité. Le service prévoit d’utiliser les composants React de l’interface utilisateur Material Google pour améliorer l’expérience de l’utilisateur des formulaires. Il utilisera également les fonctionnalités du serveur principal, telles que :

* Signatures numériques
* Intégration de données
* Gestion des processus métier
* Document d’enregistrement
* Analyse de l’utilisation

Le formulaire le plus utilisé par les touristes est le formulaire de contact, qui leur permet de poser des questions et de demander des informations. Par conséquent, le ministère des Affaires étrangères a choisi de commencer à mettre en œuvre l’approche des formulaires adaptatifs découplés avec ce formulaire. Ce tutoriel vous guide tout au long du processus de création du formulaire Contact Us à l’aide de cette nouvelle architecture. Le résultat final ressemble à ceci :

![Formulaire adaptatif découplé de contact](assets/contact-us-headless-adaptive-forms.png)