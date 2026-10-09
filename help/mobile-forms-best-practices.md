---
title: Bonnes pratiques relatives aux formulaires mobiles
description: Pour les cas d’utilisation de formulaires mobiles et hors ligne, créez votre propre application native et récupérez les définitions de formulaire via l’API de Forms adaptative découplée. Approche recommandée pour les applications mobiles natives.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: formulaires mobiles, application native, formulaires hors ligne, API découplée
index: true
exl-id: 6f25039f-61fc-4366-9e17-6b2809162c58
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
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
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
source-git-commit: b34afbc4f692b81838ad6947895c9b347dff6d62
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 5%
---
# Bonnes pratiques relatives aux formulaires mobiles {#mobile-forms-best-practices}

Pour les cas d’utilisation de formulaire mobile et hors ligne, l’approche recommandée consiste à créer votre propre application native et à récupérer les définitions de formulaire via l’API de Forms adaptative découplée. Vous pouvez ainsi contrôler entièrement l’expérience mobile et bénéficier d’une prise en charge continue à mesure que les plateformes mobiles évoluent.

## Approche recommandée {#recommended-approach}

Créez une application mobile native (iOS ou Android) qui :

1. **Récupère la définition d’un formulaire découplé** - Utilisez les [API Forms adaptatives découplées](https://opensource.adobe.com/aem-forms-af-runtime/api/) pour récupérer le fichier JSON à la demande (par exemple, lorsque l’utilisateur ouvre un formulaire ou y accède dans votre application). Vous pouvez répertorier les formulaires disponibles, puis récupérer la définition de formulaire par ID.

2. **Effectue le rendu du formulaire dans votre application** - Utilisez le framework d’interface utilisateur de votre choix (par exemple, React Native ou vues natives) pour effectuer le rendu du formulaire à partir du fichier JSON. Vous pouvez utiliser le SDK Web Forms et les composants React de formulaires adaptatifs découplés existants lorsqu’ils s’adaptent à votre pile, ou créer votre propre moteur de rendu qui utilise la même structure JSON.

3. **Prise en charge facultative hors ligne** - Implémentez un stockage local et une synchronisation dans votre application. Par exemple, mettez en cache les définitions de formulaire en ligne, enregistrez les brouillons localement et envoyez ou synchronisez les données lorsque l’appareil est de nouveau en ligne.

Cette approche permet à votre application d’être maintenue à mesure que Android et iOS changent. Elle utilise également la plateforme de Forms adaptatif découplé prise en charge pour la création, la validation et l’envoi de formulaires.

## Prise en main {#getting-started}

* [Présentation des formulaires adaptatifs découplés AEM &#x200B;](overview.md) - Fonctionnalités et concepts.
* [API de formulaires adaptatifs découplés](https://opensource.adobe.com/aem-forms-af-runtime/api/) - Répertoriez, récupérez, validez et envoyez des formulaires par programmation.
* [Architecture](architecture.md) - Comment fonctionnent les formulaires adaptatifs découplés et comment les applications front-end les utilisent.

Pour une intégration étape par étape, consultez [Création et publication d’un formulaire découplé](create-and-publish-a-headless-form.md) et le [Portail de développement](https://experienceleague.adobe.com/landing/aem-headless-forms/developer.html?lang=fr).
