---
title: Présentation du Forms adaptatif découplé AEM
description: Vue d’ensemble des formulaires adaptatifs découplés AEM.
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 55%

---


# Notes de mise à jour

Bienvenue dans la version à accès anticipé d’Experience Manager destinée aux utilisateurs et utilisatrices précoces. Poursuivez votre lecture pour obtenir des ressources et des instructions pour démarrer et tirer le meilleur parti de cette version.

Utilisez des formulaires adaptatifs découplés Adobe Experience Manager pour créer des applications de formulaire avec des structures front-end, telles que React, Angular, etc. Utilisez le SDK Web de Forms adaptatif pour la gestion des états, la validation et l’intégration à des points de contact supplémentaires.


La version à accès anticipé vous permet d’utiliser les formulaires adaptatifs découplés dans un [ environnement de développement local](setup-development-environment.md). Vous pouvez utiliser l’environnement de développement local pour créer et tester des formulaires adaptatifs découplés.

Les formulaires adaptatifs découplés font l’objet régulièrement d’améliorations. Pour vous tenir au courant des dernières nouveautés, consultez régulièrement cette page. Cette page fournit des informations sur les éléments suivants :

* accès anticipé
* dernières versions
* nouvelles fonctionnalités
* Améliorations
* correctifs de bugs
* fonctionnalité obsolète
* instructions spéciales
* Changements prévus

<!-- 

## July 2022 (v0.22.1)

### New features

* Introduced the `validateFormData` API. It validates all the components against the rules and constraints an returns the list of errors. The validation takes place on the server.
* Introduced the `FormLoad` event.
* Introduced the `importData` and `exportData`.
* You can now dynamically add or remove items, that expect unqiue values, from a repeatable panel. You can use the `minItems` and `maxitems` constraint to set limit of item.
* You can now use constraint to set maximum file upload size, accepted file types, minimum files, and maximum files to upload.

### Improvements and bug fixes

* The service was executing some event handlers twice. The issue is fixed.
* Fixing Data Generation with different values of dataRef, name and type.

<!-- ### React Renderer component -->

## Artefacts disponibles dans la version à accès anticipé

Dans le cadre du parcours visant à vous proposer les formulaires adaptatifs découplés Adobe Experience Manager, les artefacts suivants sont disponibles dans la version à accès anticipé :

### SDK AEM Forms as a Cloud Service

SDK AEM Forms as a Cloud Service pour vous aider à créer, à stocker et à récupérer des formulaires adaptatifs découplés. Il permet également de fournir des services de préremplissage, de validation des règles côté serveur et d’envoi pour les formulaires adaptatifs découplés.

### SDK web pour les formulaires

Forms Web SDK fournit des API pour valider les contraintes appliquées aux différents champs d’un formulaire, ainsi que des points d’extension pour connecter la structure JSON du formulaire au framework de l’interface utilisateur. Il fournit également React Renderer pour les formulaires adaptatifs découplés pour vous permettre d’intégrer un formulaire adaptatif découplé à votre application. Les composants de la SDK Web disponibles sont les suivants :

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### Storybook

Le [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) présente un aperçu des différents composants des formulaires adaptatifs découplés. Il fournit également une liste de tous les composants pris en charge, leurs propriétés et contraintes correspondantes.

### Composant principal des formulaires

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

Les composants principaux sont un ensemble de composants de gestion de contenu web (Web Content Management, WCM) normalisés visant à accélérer le développement et à réduire les coûts de maintenance des formulaires. Le composant Conteneur de formulaires est un composant principal. Il vous permet d’incorporer et de générer une structure JSON d’un formulaire adaptatif découplé dans l’éditeur de Forms adaptatif de Forms as a Cloud Service SDK.

### Spécifications des formulaires adaptatifs V2

La spécification des formulaires adaptatifs découplés fournit des informations détaillées sur tous les composants, contraintes et méthodes disponibles pour définir les formulaires adaptatifs découplés. La spécification est disponible au format [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf).

### API HTTP et JS

Les [API HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) vous permettent de répertorier, de récupérer, de valider, d’envoyer et de suivre le statut d’envoi des formulaires découplés. <!-- URL is 404! [JS APIs](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) helps you use Headless adaptive forms with any JavaScript based UI framework. -->

### Extension de Visual Studio Code

L’[extension de Visual Studio Code](visual-studio-code-extension-for-headless-adaptive-forms.md) permet de créer une structure JSON valide. Elle assure la prise en charge et la validation IntelliSense pour la structure JSON des formulaires et fournit des fonctions courantes telles que l’ajout, la suppression ou l’attribution d’un nouveau nom aux composants d’une structure JSON.

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->