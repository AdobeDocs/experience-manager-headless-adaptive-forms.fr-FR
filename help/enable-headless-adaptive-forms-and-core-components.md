---
title: Activer les formulaires adaptatifs découplés sur AEM Forms 6.5
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM 6.5 Forms
description: Découvrez comment activer les formulaires adaptatifs découplés sur AEM 6.5 Forms avec le guide détaillé d’Adobe. Ce tutoriel vous guide tout au long du processus, ce qui facilite l’intégration de cette puissante fonctionnalité à votre site web et améliore votre expérience utilisateur.
contentOwner: Khushwant Singh
role: Admin
exl-id: e1a5e7e0-d445-4cca-b8d7-693d9531f075
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 69%

---

# Activer les formulaires adaptatifs découplés sur AEM Forms 6.5 {#enable-headless-adaptive-forms-on-aem-65-forms}

Pour activer les formulaires adaptatifs découplés dans votre environnement AEM 6.5 Forms, configurez un projet basé sur l’archétype AEM 41 ou version ultérieure et déployez-le sur toutes vos instances de création et de publication.

En déployant le projet d’archétype AEM 41 ou version ultérieure sur vos instances AEM 6.5 Forms, vous pouvez [créer un formulaire adaptatif basé sur les composants principaux](create-a-headless-adaptive-form.md). Ces formulaires sont représentés au format JSON et utilisés à la fois comme Forms adaptatif `Headful` et `Headless`, ce qui permet une plus grande flexibilité et personnalisation sur un large éventail de canaux, y compris les applications mobiles, web et natives.

## Prérequis {#prerequisites}

Avant d’activer le Forms adaptatif découplé dans l’environnement AEM 6.5 Forms,

* [Effectuez un mise à niveau vers le pack de services 16 d’AEM 6.5 Forms (6.5.16.0) ou une version ultérieure](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions).

* Installez la dernière version d’[Apache Maven](https://maven.apache.org/download.cgi).

* Installez un éditeur de texte brut. Par exemple, Microsoft Visual Studio Code.

## Créer et déployer le dernier projet basé sur l’archétype AEM

Pour créer un projet d’archétype AEM 41 ou [version ultérieure](https://github.com/adobe/aem-project-archetype) et le déployer sur toutes vos instances de création et de publication, procédez comme suit :

1. Connectez-vous à l’ordinateur qui héberge et exécute votre instance AEM 6.5 Forms en tant qu’administrateur.
1. Ouvrez l’invite de commandes ou le terminal.
1. Exécutez la commande suivante pour créer un projet basé sur AEM Archetype 41 :

   * Microsoft Windows

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
      -D archetypeGroupId=com.adobe.aem ^
      -D archetypeArtifactId=aem-project-archetype ^
      -D archetypeVersion=41 ^
      -D appTitle="My Form" ^
      -D appId="myform" ^
      -D groupId="com.myform" ^
      -D includeFormsenrollment="y" ^
      -D aemVersion="6.5.23" 
   ```

   * Linux® ou Apple macOS

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
      -D archetypeGroupId=com.adobe.aem \
      -D archetypeArtifactId=aem-project-archetype \
      -D archetypeVersion=41 \
      -D appTitle="My Form" \
      -D appId="myform" \
      -D groupId="com.myform" \
      -D includeFormsenrollment="y" \
      -D aemVersion="6.5.23" 
   ```

   Lorsque vous exécutez la commande ci-dessus, tenez compte des points suivants :

   * Mettez à jour la commande afin de refléter les valeurs spécifiques de votre environnement, y compris pour appTitle, appId et groupId. Définissez également les valeurs de includeFormsenrollment sur `y`. Si vous utilisez le portail Formulaires, définissez l’option _includeExamples=y_ de façon à inclure les composants principaux du portail Formulaires dans votre projet.


1. (Uniquement pour les projets basés sur l’archétype 41) Une fois le projet d’archétype AEM créé, activez les thèmes des formulaires adaptatifs basés sur les composants principaux. Pour activer les thèmes, procédez comme suit :

   1. Ouvrez le [Dossier du projet d’archétype AEM]/ui.apps/src/main/content/jcr_root/apps/__appId__/components/adaptiveForm/page/customheaderlibs.html pour modification :

   1. Ajoutez le code suivant à la ligne 21 :

      ```XML
      <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
      data-sly-use.formstructparser="com.adobe.cq.forms.core.components.models.form.FormStructureParser"
      data-sly-test.themeClientLibRef="${formstructparser.themeClientLibRefFromFormContainer}">
      <sly data-sly-test="${themeClientLibRef}" data-sly-call="${clientlib.css @ categories=themeClientLibRef}"/>
      </sly>
      ```

      ![Ajouter le code mentionné ci-dessus à la ligne 21](/help/assets/code-to-enable-themes.png)

   1. Enregistrez et fermez le fichier.

1. Mettez à jour le projet pour inclure la dernière version des composants principaux Forms :

   1. Ouvrez le [Dossier du projet d’archétype AEM]/pom.xml pour modification.
   1. Définissez la version de `core.forms.components.version` et `core.forms.components.af.version` sur la dernière version des [composants principaux de Forms](https://github.com/adobe/aem-core-forms-components/tree/release/650).

   1. Enregistrez et fermez le fichier.


1. Une fois le projet d’archétype AEM créé, créez le package de déploiement pour votre environnement. Pour créer le package, procédez comme suit :

   1. Accédez au répertoire racine de votre projet d’archétype AEM.


   1. Exécutez la commande suivante pour créer le projet d’archétype AEM pour votre environnement :

      ```Shell
      mvn clean install
      ```

      ![archetypebuild-success](assets/corecomponent-build-successful.png)


   Une fois le projet d’archétype AEM créé, un package AEM est généré. Vous trouverez le package dans le [Dossier du projet d’archétype AEM]\all\target\[appid].all-[version].zip

1. Utilisez le [Gestionnaire de modules](https://experienceleague.adobe.com/fr/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager) pour déployer le package [Dossier du projet d’archétype AEM]\all\target\[appid].all-[version].zip sur toutes les instances de création et de publication.

>[!NOTE]
>
>
>
>Si vous rencontrez des difficultés pour accéder à la boîte de dialogue de connexion sur une instance de publication pour installer le package par le biais du gestionnaire de packages, essayez de vous connecter via l’URL suivante : `http://[Publish Server URL]`:[PORT]/system/console. Ce processus permet de se connecter à l&#39;instance de publication et de poursuivre le processus d&#39;installation.


Les composants principaux sont activés pour votre environnement. Un modèle vierge de formulaire adaptatif basé sur des composants principaux et un thème Canvas 3.0 sont déployés sur votre environnement. Vous pouvez maintenant [créer un formulaire adaptatif basé sur les composants principaux](create-a-headless-adaptive-form.md).

## Questions fréquentes

### Quels sont les composants principaux ?

Les [composants principaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/introduction) sont un ensemble de composants WCM (Web Content Management, gestion de contenu web) normalisés pour AEM dont l’objectif est d’accélérer le développement et de réduire les coûts de maintenance de vos sites Web.

### Quelles sont les fonctionnalités des composants principaux ?


Lorsque les composants principaux des formulaires adaptatifs sont activés pour votre environnement, un modèle vierge de formulaire adaptatif basé sur les composants principaux et le thème Canvas 3.0 sont ajoutés à votre environnement. Après avoir activé les composants principaux des formulaires adaptatifs pour votre environnement, vous pouvez :

* Créer un formulaire adaptatif basé sur des composants principaux.
* Créer des modèles de formulaires adaptatifs basés sur des composants principaux.
* Créer des thèmes personnalisés pour les modèles de formulaires adaptatifs basés sur les composants principaux.
* diffuser les représentations JSON des formulaires adaptatifs basés sur les composants principaux vers des canaux tels que le mobile, le Web, les applications natives et les services qui requièrent la représentation découplée d’un formulaire.
