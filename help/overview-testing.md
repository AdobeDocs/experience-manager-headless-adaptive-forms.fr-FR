---
title: Vue d’ensemble des formulaires adaptatifs découplés AEM
description: Créez des formulaires une fois et diffusez-les sur CMS, React, SPA, web, mobile, Alexa, WhatsApp et d’autres plateformes avec des formulaires adaptatifs AEM Headless pour une capture de données rapide et évolutive.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: Système de gestion de contenu (CMS) découplé, formulaires adaptatifs, interface utilisateur découplée, système de gestion de contenu (CMS) couplé, assistants vocaux, alexa, agents conversationnels, architecture WhatsApp
hide: true
hidefromtoc: true
exl-id: f6a383ea-684b-479d-a15f-8ebced75635e
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 57%

---

# Présentation

Grâce aux formulaires adaptatifs découplés Adobe Experience Manager (AEM), créez et gérez des formulaires web découplés au sein de la plateforme Adobe Experience Manager. Cette fonctionnalité permet à vos organisations de créer, de publier et de gérer des formulaires interactifs accessibles via des API, plutôt que par le biais d’une interface utilisateur graphique classique. Les Forms adaptatives découplées AEM offrent plus de flexibilité et d’évolutivité dans le développement et le déploiement de formulaires, ainsi qu’une expérience utilisateur améliorée grâce à la possibilité d’adapter la conception et les fonctionnalités de formulaires aux besoins spécifiques. En utilisant les fonctionnalités d’AEM et de la technologie découplée, cette solution fournit une plateforme robuste pour la création, la gestion et le déploiement de formulaires web pour divers cas d’utilisation et applications.

![Créez et générez nativement un formulaire sur n’importe quel site web, application ou interaction non visuelle](/help/assets/headless-forms-for-any-device.jpeg).

Les formulaires adaptatifs découplés vous permettent d’effectuer les opérations suivantes :

* Créez des formulaires multicanaux de haute qualité dans le langage de programmation de votre choix.
* Intégrez de manière native des formulaires à vos applications de bureau et mobiles, à vos sites web et à vos applications de chat.
* Réutilisez vos composants d’IU propriétaires avec des applications de formulaires.
* Utilisation de la [puissance d’Adobe Experience Manager Forms](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/forms/getting-started/introduction-aem-forms).

En outre, vous avez la possibilité de développer vos propres composants pour rendre un formulaire à l’aide du framework d’interface utilisateur et du langage de programmation de votre choix. Vous pouvez également utiliser les composants React prêts à l’emploi pour générer un formulaire adaptatif découplé.

<!-- 

## Key Features

<table style="width:100%;">
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Responsive Forms</h2>
          <p>The adaptive form feature enables you to create a single source for a form that automatically sizes and re-flows on mobile devices.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Communication API</h2>
          <p>The adaptive form feature enables you to create a single source for a form that automatically sizes and re-flows on mobile devices.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="Card Image 2" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Business Process Management</h2>
          <p>Integrate RDBMS, OData, Or Microsoft SOAP services, as well as protocols like Swagger 2.0 to connect to just about anything.</p>
        </div>
      </div>
    </td>
  </tr>
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="Card Image 3" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Save and resume forms</h2>
          <p>Allow clients to save in-progress forms and return later to complete them, even on another device.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/04-overview-search.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Forms Search and Discovery</h2>
          <p>Let customers easily find relevant forms based on a simple search query, tags, filters, and even geolocation — on any device through a personalized portal, with or without authentication.
          </p>
        </div>
      </div>
    </td>
      <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/04-overview-search.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Forms Search and Discovery</h2>
          <p>Let customers easily find relevant forms based on a simple search query, tags, filters, and even geolocation — on any device through a personalized portal, with or without authentication.
          </p>
        </div>
      </div>
    </td>
  </tr>
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/05-overview-analytics.jpeg" alt="Card Image 2" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Form analytics and reporting</h2>
          <p>Out-of-the-box, customizable dashboards make it easy to apply analytics to forms to gain insight for actionable areas of improvement.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/06-overview-business-process.jpeg" alt="Card Image 3" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Business Process Management</h2>
          <p>Route application submissions through customized workflows and a centralized dashboard for review, approval, and digital signatures by back-office employees — even when employees are on the go on a mobile device.
          </p>
        </div>
      </div>
    </td>
  </tr>
</table>




<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: 20px;">
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Icon 1" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 1</h2>
        <p>Description 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="Icon 2" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 2</h2>
        <p>Description 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="Icon 3" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 3</h2>
        <p>Description 3</p>
    </div>
        <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/04-overview-search.jpeg" alt="Icon 1" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 1</h2>
        <p>Description 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/05-overview-analytics.jpeg" alt="Icon 2" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 2</h2>
        <p>Description 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/06-overview-business-process.jpeg" alt="Icon 3" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 3</h2>
        <p>Description 3</p>
    </div>
    <!-- Add more cards as needed -->
</div>




<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: 20px;">
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Image 1" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">En-tête 1</h2>
        <p>Description 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="Image 2" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">En-tête 2</h2>
        <p>Description 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="Image 3" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">En-tête 3</h2>
        <p>Description 3</p>
    </div>
    <!-- Add more cards as needed -->
</div>

-->

## Qui peut utiliser des formulaires adaptatifs découplés ? {#who-can-use-headless-adaptive-forms}

Une développeuse ou un développeur front-end rompu aux frameworks JavaScript modernes peut utiliser des formulaires adaptatifs découplés. Les développeurs et développeuses peuvent tirer parti de leur expertise dans les langages front-end tels que React pour créer de superbes expériences de capture de données à l’échelle de l’entreprise.

Aucune connaissance préalable d’Adobe Experience Manager n’est nécessaire pour développer des formulaires adaptatifs découplés.

<!-- 
## How to join the early adopter program? {#how-to-join-early-adopter-forms}

The service is available for AEM Forms as a Cloud Service and AEM 6.5.16.0 Forms or later On-Premise term customers and Adobe-Managed Service enterprise customers. Send an email to [headlessadaptiveforms@adobe.com](mailto:headlessadaptiveforms@adobe.com) from your official email ID to join the early adopter program. 

-->
