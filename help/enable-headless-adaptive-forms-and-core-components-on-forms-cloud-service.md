---
title: Activer les formulaires adaptatifs découplés sur AEM Forms as a Cloud Service
description: Guide détaillé pour l’activation des formulaires adaptatifs découplés dans AEM Forms as a Cloud Service, qui simplifie la configuration et l’activation dans votre environnement.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin
level: Beginner, Intermediate
contentOwner: Khushwant Singh
docset: CloudService
hide: true
hidefromtoc: true
exl-id: 7afff771-1296-4162-84c5-c8266b94af2f
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 74%

---

# Activer les formulaires adaptatifs découplés sur AEM Forms as a Cloud Service {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

L’activation des formulaires adaptatifs découplés sur AEM Forms as a Cloud Service vous permet de commencer à créer, à publier et à diffuser des formulaires découplés à l’aide de vos instances Cloud Service d’AEM Forms sur plusieurs canaux. L’environnement des composants principaux des formulaires adaptatifs doit être activé pour utiliser les formulaires adaptatifs découplés.

## Remarques

* Lorsque vous créez un programme AEM Forms as a Cloud Service, [les formulaires adaptatifs découplés sont déjà activés pour votre environnement](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Si vous exécutez un ancien programme Forms as a Cloud Service dans lequel les composants principaux ne sont [pas activés](#enable-components), commencez par [ajouter les dépendances des composants principaux de Forms adaptatif](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) à votre référentiel Cloud Service. Déployez le référentiel mis à jour dans chaque environnement pour activer les formulaires adaptatifs découplés.

* Si votre environnement Cloud Service vous permet déjà de [créer des formulaires adaptatifs basés sur les composants principaux](create-a-headless-adaptive-form.md), les formulaires adaptatifs découplés sont automatiquement activés. Vous pouvez ensuite diffuser ces formulaires en tant qu’expériences découplées sur des applications mobiles, web, natives ou tout service qui les requiert.

>[!NOTE]
>
>
> Adobe fournit un Forms adaptatif [kit de démarrage (application React)](create-and-publish-a-headless-form.md) pour aider les développeurs à commencer rapidement le développement de Forms adaptatif découplé, sans activer le Forms adaptatif découplé dans l’environnement AEM Forms as a Cloud Service. Vous pouvez activer les formulaires adaptatifs découplés dans un environnement Forms as a Cloud Service ultérieurement après avoir suivi un [atelier pratique rapide sur le développement de formulaires découplés](create-and-publish-a-headless-form.md).

## Activer les formulaires adaptatifs découplés dans un environnement AEM Forms as a Cloud Service

Effectuez les étapes suivantes, dans l’ordre indiqué, pour activer les formulaires adaptatifs découplés pour un environnement AEM Forms as a Cloud Service.

<!-- Missing image ALT tag -->
![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## &#x200B;1. Cloner votre référentiel Git AEM Forms as a Cloud Service {#clone-git-repository}

1. Connectez-vous à [Cloud Manager](https://my.cloudmanager.adobe.com/) et sélectionnez votre organisation et votre programme.

1. Accédez à la carte **Pipelines** à partir de la page **Vue d’ensemble du programme**.

1. Cliquez sur le bouton **Accéder aux informations sur le référentiel** pour accéder à votre référentiel Git et le gérer. La page contient les informations suivantes :

   * URL vers le référentiel Git de Cloud Manager.
   * Informations d’identification du nom d’utilisateur du référentiel Git (nom d’utilisateur et mot de passe).

   Cliquez sur **Générer un mot de passe** pour afficher ou générer le mot de passe.

1. Ouvrez le terminal ou l’invite de commande sur votre ordinateur local et exécutez la commande suivante :

   ```Shell
   git clone [Git Repository URL]
   ```

   Lorsque l’on vous y invite, saisissez les informations d’identification. Le référentiel est cloné sur votre ordinateur local.


## &#x200B;2. Ajouter les dépendances des composants principaux des formulaires adaptatifs à votre référentiel Git {#add-adaptive-forms-core-components-dependencies}

1. Ouvrez votre dossier du référentiel Git dans un éditeur de code de texte brut. Par exemple, VS Code.
1. Ouvrez le fichier `[AEM Repository Folder]\pom.xml` en mode d’édition.
1. Remplacez les versions des composants `core.forms.components.version`, `core.forms.components.af.version` et `core.wcm.components.version` par les versions spécifiées dans la [documentation des composants principaux](https://github.com/adobe/aem-core-forms-components). Si le composant n’existe pas, ajoutez ces composants.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![Mention de la dernière version des composants principaux de Forms](/help/assets/latest-forms-component-version.png)

1. Dans la section des dépendances du fichier `[AEM Repository Folder]\pom.xml`, ajoutez les dépendances suivantes, puis enregistrez le fichier.

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. Ouvrez le fichier `[AEM Repository Folder]/all/pom.xml` en mode d’édition. Ajoutez les dépendances suivantes dans la section `<embeddeds>` et enregistrez le fichier.

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  Remplacez `${appId}` par votre appId.
   >
   >  Pour rechercher votre `${appId}`, dans le fichier `[AEM Repository Folder]/all/pom.xml`, recherchez le terme `-packages/application/install`. Le texte situé avant le terme `-packages/application/install` est votre `${appId}`. Par exemple, le code suivant, `myheadlessform` est `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Dans la section `<dependencies>` du fichier `[AEM Repository Folder]/all/pom.xml`, ajoutez les dépendances suivantes, puis enregistrez le fichier :

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. Ouvrez le `[AEM Repository Folder]/ui.apps/pom.xml` pour édition. Ajoutez la dépendance `af-core bundle` et enregistrez le fichier.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >Assurez-vous que les artefacts de composants principaux des formulaires adaptatifs suivants ne sont pas inclus dans votre projet.
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > et
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. Enregistrez et fermez le fichier.

## &#x200B;3. Mettez à jour le projet pour inclure la dernière version des composants principaux de Forms :

1. Ouvrez le [dossier de projet d’archétype AEM]/pom.xml pour modification.


1. Enregistrez et fermez le fichier.

## &#x200B;4. Validez les mises à jour dans votre référentiel Git et exécutez un pipeline pour déployer le référentiel {#Commit-the-updates-to-your-git-repository}

1. Pour valider le code dans votre référentiel Git :
   1. Ouvrez le terminal ou l’invite de commande.
   1. Accédez à `[AEM Repository Folder]` et exécutez les commandes suivantes dans l’ordre indiqué

      ```Shell
      git add pom.xml
      git add all/pom.xml
      git add ui.apps/pom.xml
      git commit -m "Added dependencies for Adaptive Forms Core Components"
      git push origin
      ```

1. Une fois les fichiers validés dans le référentiel Git, [exécutez le pipeline](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-manager/content/using/code-deployment).

   Une fois l’exécution du pipeline réussie, les composants principaux de Forms adaptatifs sont activés pour l’environnement correspondant. En outre, un modèle de formulaire adaptatif (composants principaux) et un thème Canvas 3.0 sont ajoutés à votre environnement Forms as a Cloud Service, ce qui vous permet de personnaliser et de créer des composants principaux basés sur les formulaires adaptatifs.


## Questions fréquentes {#faq}

### Quels sont les composants principaux ? {#core-components}

Les [composants principaux](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/introduction) sont un ensemble de composants WCM (Web Content Management, gestion de contenu web) normalisés pour AEM dont l’objectif est d’accélérer le développement et de réduire les coûts de maintenance de vos sites Web.

### Quelles sont toutes les fonctionnalités ajoutées lors de l’activation des composants principaux ? {#core-components-capabilities}

Lorsque les composants principaux des formulaires adaptatifs sont activés pour votre environnement, un modèle de formulaire adaptatif basé sur les composants principaux vierge et le thème Canvas 3.0 sont ajoutés à votre environnement. Après avoir activé les composants principaux des formulaires adaptatifs pour votre environnement, vous pouvez :

* Créer un formulaire adaptatif basé sur des composants principaux.
* Créer des modèles de formulaires adaptatifs basés sur des composants principaux.
* Créer des thèmes personnalisés pour les modèles de formulaires adaptatifs basés sur les composants principaux.
* Diffuser les représentations JSON des formulaires adaptatifs basés sur les composants principaux à divers canaux tels que les applications mobiles, web et natives, ainsi que les services qui nécessitent une représentation découplée d’un formulaire.

### Les composants principaux des formulaires adaptatifs sont-ils activés pour mon environnement ? {#enable-components}

Pour vérifier que les composants principaux des formulaires adaptatifs sont activés pour votre environnement :

1. [Clonez votre référentiel AEM Forms as a Cloud Service](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Ouvrez le fichier `[AEM Repository Folder]/all/pom.xml` du référentiel Git AEM Forms Cloud Service.

1. Recherchez les dépendances suivantes :

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![Localisez l’artefact core-forms-components-af-core dans all/pom.xml](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png).

   Si les dépendances existent, les composants principaux des formulaires adaptatifs sont activés pour votre environnement.
