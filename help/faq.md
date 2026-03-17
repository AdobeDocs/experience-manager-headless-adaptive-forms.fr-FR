---
title: Questions Fréquentes Sur Le Forms Adaptatif Découplé
description: Questions fréquentes
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: découplé, formulaire adaptatif, questions fréquentes
index: true
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 41%

---

# Questions fréquentes {#headless-adaptive-forms-faq}

## Dois-je connaître React.js pour utiliser les formulaires adaptatifs découplés ?

Vous pouvez utiliser n’importe quel framework, bibliothèque ou langue pour générer des formulaires adaptatifs découplés et utiliser les API REST Adobe pour valider et envoyer les formulaires. La bibliothèque AF-core, prête à l’emploi, est indépendante du framework. Les bibliothèques React-Render et React-component, également prêtes à l’emploi, sont fournies pour votre commodité. Vous pouvez créer vos propres composants ; vous n’êtes pas limité à ceux fournis.


<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## Ai-je besoin du sandbox Forms as a Cloud Service pour utiliser des formulaires adaptatifs découplés ?

Vous pouvez utiliser l’application de démarrage pour commencer à développer et à styliser vos formulaires adaptatifs découplés. Vous avez besoin de Forms as a Cloud Service pour héberger et utiliser des formulaires adaptatifs découplés ainsi que des fonctionnalités de formulaires back-end.

<!-- 
## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. 
-->

## Où puis-je obtenir un aperçu d’un formulaire adaptatif découplé ? {#storybook-example}

Vous pouvez utiliser l’application de démarrage pour afficher et prévisualiser un formulaire adaptatif découplé personnalisé. Vous pouvez également modifier un exemple de [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) pour prévisualiser un formulaire adaptatif découplé.

![](/help/assets/storybook-example.png)

## Est-il possible d’utiliser des formulaires adaptatifs découplés avec des frameworks personnalisés ?

Les formulaires adaptatifs découplés sont basés sur une [spécification standard](/help/assets/headless-adaptive-forms-specification.pdf). Vous pouvez étendre la spécification et l’utiliser pour créer des composants personnalisés. Par exemple, des composants pour Chakra UI, Vue.js, etc.

## Les formulaires adaptatifs découplés prennent-ils en charge les champs en cascade ?

Dans les champs en cascade, le contenu du second champ dépend du contenu choisi dans le premier champ. Le [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down) fournit un exemple de champs en cascade.

## Les formulaires adaptatifs découplés permettent-ils de préremplir des formulaires avec des données personnalisées ?

Les formulaires adaptatifs découplés permettent de préremplir des formulaires avec des données personnalisées. Le [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) fournit un exemple de la façon de préremplir un formulaire adaptatif découplé.

<!--
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  
-->

## Puis-je utiliser des formulaires adaptatifs découplés avec Angular SPA ?

Vous pouvez utiliser le SDK web pour intégrer des formulaires adaptatifs découplés avec Angular SPA. Il est indépendant de tout framework. Vous pouvez utiliser le SDK React comme référence.

<!--
## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 
-->

## Existe-t-il un plug-in pour faciliter le développement des formulaires adaptatifs découplés ?

Oui — une extension Visual Studio Code vous permet de créer manuellement des formulaires adaptatifs découplés dans JSON.

## Quelle est l’approche recommandée pour les formulaires mobiles ou hors ligne ? {#mobile-offline-forms}

Créez votre propre application native et récupérez les définitions de formulaire via l’API de Forms adaptatif découplé. Vous pouvez éventuellement implémenter une prise en charge hors ligne (par exemple, le stockage local et la synchronisation). Consultez la section [ Bonnes pratiques relatives aux formulaires mobiles ](mobile-forms-best-practices.md) pour connaître l’approche recommandée et les liens vers les API.

## Comment utiliser les API GraphQL ou découplées avec AEM Forms ?

AEM Headless Adaptive Forms utilise les API **HTTP/REST**, pas GraphQL. Votre application appelle ces API pour répertorier les formulaires, récupérer une définition de formulaire (JSON), valider, envoyer et suivre le statut d’envoi. Utilisez les [API HTTP de formulaires adaptatifs découplés](https://opensource.adobe.com/aem-forms-af-runtime/api/) pour consulter l’ensemble des informations. Pour savoir comment les formulaires sont récupérés et rendus, consultez [Architecture](architecture.md) et [Présentation des formulaires découplés](understanding-headless-forms.md).

## Comment puis-je implémenter et mettre en forme des formulaires découplés à l’aide des composants React dans Adobe AEM Forms ?

Vous implémentez et mettez en forme des formulaires découplés à l’aide de vos propres composants React et CSS (ou d’une bibliothèque d’IU telle que l’IU Material). La logique du formulaire (état, validation et règles) provient de Forms Web SDK et du fichier JSON du formulaire ; votre application fournit l’interface utilisateur qui la génère.

* Pour appliquer un style à un formulaire découplé avec une bibliothèque d’interface utilisateur React, consultez [Utilisation d’une bibliothèque React personnalisée pour effectuer le rendu d’un formulaire découplé](use-google-material-ui-react-components-to-render-a-headless-form.md).
* Pour créer et mapper des composants React personnalisés à des champs de formulaire, consultez [Utilisation de composants personnalisés pour générer un formulaire découplé](developing-for-headless-forms-using-your-own-components.md).

Pour des concepts tels que quand utiliser les formulaires découplés, la gestion des états et la validation, voir [Comprendre les formulaires découplés](understanding-headless-forms.md).

## Comment mettre en œuvre et personnaliser AEM Forms avec des CSS, des thèmes, des éditeurs de règles et des formulaires découplés personnalisés ?

**Formulaires découplés :** le style et l’apparence sont entièrement sous votre contrôle. Vous utilisez vos propres composants React (ou d’autres) et votre propre CSS ; il n’y a pas de thèmes intégrés. Consultez les sections [Utiliser une bibliothèque React personnalisée pour effectuer le rendu d’un formulaire découplé](use-google-material-ui-react-components-to-render-a-headless-form.md) et [Utiliser des composants personnalisés pour effectuer le rendu d’un formulaire découplé](developing-for-headless-forms-using-your-own-components.md) pour implémenter et mettre en forme des formulaires découplés.

**AEM Forms classique (thèmes, éditeur de règles, éditeur visuel) :** le code CSS personnalisé, l’éditeur de thèmes et l’éditeur de règles s’appliquent à l’expérience de création Forms adaptative classique (non découplée). Pour ces rubriques, consultez la [documentation d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-forms.html) sur Experience League.

## Un formulaire adaptatif découplé peut-il se connecter à n’importe quel CRM pour lire ou écrire des données ?

Vous pouvez utiliser Microsoft Dynamics et Salesforce pour envoyer ou préremplir un formulaire adaptatif découplé. Outre les CRM, les formulaires adaptatifs découplés prennent en charge l’envoi ou le préremplissage à l’aide de points d’entrée REST, d’e-mails et d’actions d’envoi personnalisées.
