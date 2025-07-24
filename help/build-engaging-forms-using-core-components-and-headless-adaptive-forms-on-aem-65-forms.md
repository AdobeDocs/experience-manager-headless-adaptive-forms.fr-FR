---
title: Créer des formulaire attrayants à l’aide des composants principaux et découplés
description: Créez un Forms attrayant à l’aide des composants principaux et découplé.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
topic-tags: develop
hide: true
exl-id: 07a71aac-de38-4839-b8d6-b47c3f575eb3
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 67%

---

# Créez des formulaires attrayants à l’aide de composants de base et de formulaires adaptatifs découplés dans AEM Forms 6.5. {#build-engaging-forms-using-core-components-and-headless}

<!-- This article and many others in this entire repo are completely missing the image ALT tags (descriptions) for each added image asset. That is impacting the CQI score for Experience Manager in a negative way. Be sure you take the time to add the required missing image ALT tags.  -->

## Présentation de l’atelier {#lab-overview}

Dans cet atelier pratique, vous apprendrez à utiliser AEM Forms avec les derniers composants principaux, alignés sur AEM Sites, pour créer rapidement des formulaires adaptatifs. Diffusez ces formulaires en tant qu’expériences découplées sur les canaux web, mobiles et de chat pour une capture de données omnicanal transparente. Vous allez également découvrir les bonnes pratiques en matière de style, de personnalisation et de développement front-end.

## Principaux points à retenir {#key-takeaways}

* **Agilité professionnelle** : en tant qu’utilisateur professionnel ou utilisatrice professionnelle, je peux facilement créer une expérience de formulaire pour plusieurs canaux.

* **Puissance du développeur front-end** : en tant que développeur ou développeuse front-end, je peux contrôler l’expérience de l’utilisateur final ou de l’utilisatrice finale à l’aide de formulaires découplés.

* **Vitesse du développeur** : en tant que développeur ou développeuse, je peux personnaliser facilement et systématiquement les composants Sites et Forms.

## Avant de commencer {#pre-requisites}

Pour utiliser cet atelier pratique, procédez comme suit :

* Installez la [dernière version de Git](https://git-scm.com/downloads). Si vous découvrez Git, consultez l’article [Installer Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Installez [Node.js 16.13.0 ou version ultérieure](https://nodejs.org/en/download/). <!-- URL IS 404! If you are new to Node.js, see [How to install Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).-->

* [Activez le Forms adaptatif découplé](enable-headless-adaptive-forms-and-core-components.md) dans votre environnement AEM 6.5 Forms.

* Installez [Microsoft Code Visual Studio](https://code.visualstudio.com/download) ou un autre éditeur de texte brut. Les exemples de ce document utilisent Microsoft Visual Studio Code.

## Leçon 1 {#lesson-1}

### Objectif {#lesson-1-objectives}

Familiarisez-vous avec l’environnement AEM 6.5 Forms.

### Contexte de la leçon {#lesson-1-context}

Dans cette leçon, vous vous familiarisez avec AEM Forms as a Cloud Service 6.5 en naviguant dans l’interface utilisateur.

### Exercice {#lesson-1-excercise}

1. Ouvrez votre navigateur et saisissez l’URL de l’environnement de création. Par exemple :
   [https://localhost:4502](https://localhost:4502).

1. Une fois la connexion établie, accédez à l’interface utilisateur d’AEM Forms. Cliquez sur **Forms**.

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. Cliquez sur **Formulaires &amp; Documents**. Ignorez les fenêtres contextuelles liées aux préférences ou aux informations.

   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   Tous les formulaires disponibles sont affichés.

   ![](/help/assets/screenshot2028114029.png){width="50%" align="left"}

## Leçon 2

### Objectif

Créez un formulaire adaptatif à l’aide des derniers composants principaux, puis configurez et soumettez le formulaire.

### Contexte de la leçon

En tant qu’utilisateur professionnel ou utilisatrice professionnelle, vous allez utiliser l’éditeur de Forms adaptatif et ses composants principaux prêts à l’emploi pour créer un formulaire adaptatif. Vous pouvez ensuite diffuser le formulaire vers les canaux web, mobiles et de chat pour capturer des données.

### Exercice

1. Créez un point d’entrée d’envoi pour le formulaire :

   1. Ouvrez <https://pipedream.com/requestbin> dans un nouvel onglet du navigateur.

      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. Cliquez sur **Créer un répertoire bin public** et copiez l’URL du point d’entrée.

      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

   Ce point d’entrée particulier sert d’exemple pour l’envoi et l’affichage de données. En production réelle, vous utilisez votre propre point d’entrée ou vos propres sources de données pour stocker les données capturées.

1. Créer un formulaire adaptatif :

   1. Dans l’onglet du navigateur utilisé dans la leçon 1, accédez à l’interface web d’AEM Forms et à **Forms** > **Forms et Documents**.

   1. Appuyez sur **Créer** et sélectionnez Formulaire adaptatif.

      ![](/help/assets/creating-adaptive-form-6-5.png){width="50%" align="left"}

   1. Sélectionnez le modèle **vierge avec composants principaux** à partir de l’écran de sélection des modèles, comme illustré ci-dessous, puis cliquez sur **Suivant**.

      ![](/help/assets/creating-adaptive-form-6-5-select-blank-template.png){width="50%" align="left"}

   1. Spécifiez `Contact us` comme propriété **Titre** du formulaire. Assurez-vous que le champ **Nom** du formulaire est `contact-us`.

      ![](/help/assets/creating-adaptive-form-65-specify-title.png){width="50%" align="left"}

   1. Cliquez sur **Créer**. Une boîte de dialogue s’affiche.

   1. Dans la boîte de dialogue, cliquez sur **Modifier**. Le formulaire s’ouvre dans l’éditeur de formulaire adaptatif. Ignorez les fenêtres contextuelles ou les boîtes de dialogue concernant les préférences ou les informations.

   1. Ouvrez le navigateur de composants et faites glisser puis déposez le composant Panneau au milieu de l’écran.

      ![](/help/assets/lab65-add-panel.png){width="50%" align="left"}

   1. Faites glisser puis déposez des composants à partir du navigateur de composants pour créer un formulaire, comme suit :

      ![](/help/assets/contact-us-headless-adaptive-form.png){width="50%" align="left"}


   1. Ouvrez l’explorateur de contenu, cliquez sur l’icône Propriétés du conteneur de guide , puis ouvrez l’onglet **Envoi**.

   1. Sélectionnez l’action d’envoi **Envoyer vers le point d’entrée REST**

   1. Sélectionnez l’option **Activer la requête POST** et spécifiez le point d’entrée REST créé dans la leçon 2 de la zone de texte **URL de la requête POST**, puis cliquez sur l’icône **Terminé**.

      ![](/help/assets/configure-submit-action.png){width="50%" align="left"}

1. Publier un formulaire adaptatif :

   1. Ouvrez l’interface utilisateur d’AEM, accédez à **Formulaires** > **Formulaires et documents**. Sélectionnez le formulaire créé à l’étape précédente et cliquez sur **`Publish`**.

   1. Dans la boîte de dialogue **Publier Assets**, cliquez sur **Publier**. Le message de réussite s’affiche.

## Leçon 3

### Objectif

Mise à jour des styles à l’aide des bonnes pratiques de développement front-end.

### Contexte de la leçon

Dans cette leçon, en tant que développeur front-end, vous apprendrez comment mettre facilement à jour le style du formulaire adaptatif créé précédemment.

### Exercice

Configurez un référentiel local du thème :

1. Ouvrez l’invite de commande ou un shell avec les droits d’administrateur :

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. Dans l’invite de commande, utilisez la commande suivante pour accéder au dossier `c:\git`.

   ```Shell
   cd git
   ```

   Si le dossier n’existe pas, utilisez la commande `md git` pour la créer.

1. Utilisez la commande suivante pour cloner le code front-end du thème :

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```

1. Utilisez la commande suivante dans l’ordre indiqué pour accéder au répertoire **aem-forms-theme-canvas** et ouvrez Visual Studio Code.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png){width="50%" align="left"}

1. Sélectionnez **Approbation des auteurs de tous les fichiers du dossier parent** et cliquez sur **Oui, je fais confiance aux auteurs**.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. Renommez le fichier `env_template` en .env.  Pour renommer le fichier, cliquez avec le bouton droit de la souris sur le fichier **env_template** et sélectionnez l’option **Renommer**.

   ![](/help/assets/screenshot2028116429.png){width="30%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. Définissez les valeurs suivantes pour les variables dans le fichier .env et enregistrez le fichier :

   * **AEM_URL** : spécifiez l’URL d’une instance **publish**. Par exemple, `https://localhost:4502/`.

   * **AEM_ADAPTIVE_FORM** : spécifiez le nom du formulaire. Par exemple, `contact-us`.

   </br>

   ![](/help/assets/lab65-theme-environment-variable.png)


1. Dans la fenêtre de l’invite de commande, exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Si vous recevez un message vous demandant de mettre à jour `npm` via la commande `npm notice Run npm nstall -g npm@9.6.0`, ignorez-le.
   > * N’exécutez pas d’autres commandes `npm`, sauf si le classeur vous indique de le faire.

1. Exécutez maintenant la commande suivante pour prévisualiser le formulaire.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   Une fois la commande ci-dessus exécutée, attendez le message `webpack compiled`. Le formulaire s’affiche dans un onglet du navigateur.

   >[!NOTE]
   >
   >Si un écran vierge s’affiche dans le navigateur après l’exécution de la commande `npm run live` pendant plus de 3 à 4 minutes, remplacez `localhost` dans l’URL du navigateur par 127.0.0.1 et appuyez sur **Entrée**.


   ![](/help/assets/contact-us-headless-adaptive-form-with-canvas-theme.png){width="50%" align="left"}


1. Dans Visual Studio Code, ouvrez le fichier `PROJECT\src\site\_variables.scss`. Vous remarquerez que la couleur `$error` est une nuance de rouge.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Dans le navigateur, envoyez le formulaire pour afficher la couleur rouge dans le champ **Prénom**.

   ![](/help/assets/error-color-before.png)

1. Définissez la couleur **$error** sur **#5736eb** et enregistrez le fichier.

1. Actualisez le navigateur et envoyez le formulaire. Notez que la couleur d’erreur du champ Prénom a été modifiée en conséquence.

   ![](/help/assets/error-color-after.png)

1. Dans l’invite de commande, appuyez sur **Ctrl+C**, saisissez **Y**, puis appuyez sur la touche **Entrée** pour arrêter le processus npm. Il est important d’arrêter le serveur npm afin qu’il n’entre pas en conflit avec le prochain ensemble d’exercices.
1. Fermez les fenêtres Visual Studio Code et Invite de commande.

## Leçon 4

### Objectif

Restituer le formulaire sur des interfaces web/mobile et d’autres interfaces en tant que formulaire découplé

### Contexte de la leçon

Dans cette leçon, en tant que développeur ou développeuse front-end, vous apprenez à effectuer le rendu du formulaire adaptatif créé précédemment en tant que formulaire découplé à l’aide d’un framework de conception React Spectrum.

### Exercice

Configurez un référentiel local à l’aide du projet de démarrage React :

1. Ouvrez l’invite de commande à l’aide des droits d’administration.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. Dans l’invite de commandes, utilisez la commande suivante pour naviguer dans le dossier `c:\git`.

   ```Shell
   cd git
   ```

1. Utilisez la commande suivante pour cloner le projet de démarrage react du formulaire adaptatif :

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028117329.png)

1. Utilisez les commandes suivantes dans l’ordre indiqué pour accéder au répertoire **react-starter-kit-aem-headless-forms** et ouvrez Visual Studio Code.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028117529.png)


   La fenêtre Visual Studio Code s’ouvre.

   ![](/help/assets/screenshot2028117429.png){width="50%" align="left"}

Pour effectuer le rendu du formulaire hébergé dans votre environnement de publication :

1. Renommez le fichier env_template en fichier .env . Pour renommer, cliquez avec le bouton droit de la souris sur le fichier **env_template** et sélectionnez l’option **Renommer**.

   ![](/help/assets/screenshot2028117629.png){width="30%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. Définissez les valeurs suivantes pour les variables du fichier .env. Après avoir mis à jour les variables, enregistrez le fichier.

   * **AEM_URL** : spécifiez l’URL de l’environnement de publication. Par exemple, `https://localhost:4503/`.

   * **AEM_FORM_PATH** : spécifiez le chemin d’accès du formulaire adaptatif créé dans la leçon précédente. Par exemple, `/content/forms/af/contact-us/`.

   </br>

   ![](/help/assets/lab65-starter-kit-environment-variable.png)

1. Ouvrez la fenêtre de commande, assurez-vous que vous êtes au répertoire **react-starter-kit-aem-headless-forms**, puis exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. Dans la fenêtre de l’invite de commande, exécutez la commande suivante :

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-starter-kit-start.png)

   La commande ci-dessus lance un serveur de développement local qui effectue le rendu de la définition de formulaire récupérée à partir d’AEM de manière déouplée à l’aide de la bibliothèque front-end react-spectrum.

   >[!NOTE]
   >
   > 
   > Si un écran vierge s’affiche dans le navigateur après l’exécution de la commande `npm start` pendant plus de 3 à 4 minutes, remplacez `localhost` dans l’URL du navigateur par 127.0.0.1 et appuyez sur **Entrée**.

   ![](/help/assets/headless-adaptive-form-lab.png)

Modifions le formulaire sur le serveur en tant qu’utilisateur professionnel et affichons les modifications répercutées automatiquement dans le formulaire découplé.

1. Ouvrez l’interface de gestion d’AEM Forms dans le navigateur. Par exemple, [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).

1. Sélectionnez le formulaire **Contactez-nous** et cliquez sur **Modifier.** Cette action ouvre le formulaire dans l’éditeur de formulaires adaptatifs.


1. Sélectionnez le champ **Numéro de téléphone** et cliquez sur l’**icône Modifier (icône de crayon)** dans la barre d’outils. Si la barre d’outils pop-up ne s’affiche pas, basculez en mode d’édition . Cliquez sur le bouton **Modifier** en haut à droite, à gauche du bouton **Prévisualisation**.

   ![](/help/assets/change-field-title.png){width="50%" align="left"}

1. Modifiez le libellé en **Numéro de mobile**. Cliquez sur n’importe quel espace vide du formulaire pour enregistrer les modifications apportées au formulaire.

Publions maintenant le formulaire mis à jour pour propager les modifications dans l’environnement publié.

1. Dans l’onglet de l’interface de gestion d’AEM Forms, sélectionnez le formulaire de contact, puis cliquez sur **Dépublier**. Si vous ne voyez pas le bouton **Dépublier**, passez à l’étape 3 pour publier directement les modifications.


1. Cliquez sur **Dépublier**. Cliquez sur **Fermer** dans la boîte de dialogue correspondante.

1. Une fois le navigateur actualisé, sélectionnez le formulaire de contact et cliquez sur **Publier**.


1. Cliquez sur **Publier**. Cliquez sur **Fermer** dans la boîte de dialogue correspondante.

1. Actualisez l’onglet du navigateur avec le formulaire découplé affiché. Notez que le libellé Numéro de téléphone a été remplacé par Numéro mobile.

   ![](/help/assets/headless-adaptive-form.png)

1. Ouvrez la fenêtre d’invite de commande utilisée pour démarrer le projet **react-starter-kit-aem-headless-forms**, appuyez sur **Ctrl+C**, puis
saisissez **Y** et appuyez sur la touche Entrée pour terminer le processus npm. Il est important d’arrêter le serveur npm afin qu’il n’entre pas en conflit avec le prochain ensemble d’exercices.

1. Fermez les fenêtres Visual Studio Code et Invite de commande.


## Leçon 5

### Objectif

Effectuez le rendu du formulaire en tant que formulaire découplé à l’aide de l’interface utilisateur Material Google.

### Contexte de la leçon

Dans cette leçon, en tant que développeur ou développeuse front-end, vous apprenez à effectuer le rendu du formulaire adaptatif créé précédemment en tant que formulaire découplé à l’aide de l’interface utilisateur Material de Google.

### Exercice

Configurez un référentiel local à l’aide du projet de démarrage de l’interface utilisateur Material :

1. Ouvrez l’invite de commande à l’aide des droits d’administration.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. Dans l’invite de commandes, utilisez la commande suivante pour naviguer dans le dossier `c:\git`.

   ```Shell
   cd git
   ```

1. Exécutez les commandes suivantes dans l’ordre indiqué pour créer un dossier nommé `mui` et accédez au dossier `mui` à l’aide des commandes suivantes :

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Utilisez la commande suivante pour cloner le projet de démarrage React du formulaire adaptatif :

   ```Shell
   git clone -b mui-lab https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028126529.png)

1. Utilisez la commande suivante dans l’ordre indiqué pour accéder au dossier **react-starter-kit-aem-headless-forms**, puis ouvrez le code dans Visual Studio Code :

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028126829.png)

Pour effectuer le rendu du formulaire hébergé dans votre environnement de publication :

1. Renommez le fichier **env_template** en fichier **.env**. Pour renommer, cliquez avec le bouton droit de la souris sur le fichier **env_template**, puis sélectionnez **Renommer**.

   ![](/help/assets/screenshot2028126629.png){width="30%" align="left"}

1. Définissez les valeurs suivantes pour les variables du fichier .env. Après avoir mis à jour les variables, enregistrez le fichier. Appuyez sur **Ctrl + S** pour enregistrer le fichier.

   * **AEM_URL** : spécifiez l’URL de l’environnement de publication. Par exemple, [https://localhost:4503](https://localhost:4503)

   * **AEM_FORM_PATH** : spécifiez le chemin d’accès au formulaire adaptatif créé dans la leçon précédente. Par exemple, /content/forms/af/contact-us/


1. Ouvrez la fenêtre de commande, assurez-vous que vous êtes au répertoire **react-starter-kit-aem-headless-forms**, puis exécutez la commande suivante :

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. Dans la fenêtre de l’invite de commande, exécutez la commande suivante :

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-mui-starter-kit-start.png)

   La commande démarre un serveur de développement local et effectue le rendu de la définition de formulaire récupérée à partir d’AEM de façon découplée à l’aide de la bibliothèque front-end de l’interface utilisateur Material de Google.

   >[!NOTE]
   >
   >Si un écran vierge s’affiche dans le navigateur après l’exécution de la commande `npm start` pendant plus de 3 à 4 minutes, remplacez `localhost` dans l’URL du navigateur par 127.0.0.1 et appuyez sur **Entrée**.

   ![](/help/assets/google-mui-form.png)

## Leçon 6

### Objectif

Créez un autre aspect du formulaire découplé à l’aide des variantes de composants de l’interface utilisateur Material.

### Contexte de la leçon

En tant que développeur front-end, vous allez apprendre à créer d’autres versions d’interface utilisateur Material de divers composants dans cette leçon. Vous allez également les appliquer au formulaire adaptatif créé précédemment par l’utilisateur chargé de la conception de parcours.

### Exercice

Mettez à jour la variante des composants dans le projet découplé. Pour modifier la variante du composant de saisie de texte de l’interface utilisateur Material en `OutlinedInput` :

1. Dans Visual Code, accédez au composant de saisie de texte en ouvrant le fichier `index.tsx` à l’emplacement `src/components/textinput/index.tsx`.

1. Ajoutez `//` au début de la ligne de code 104. Cela convertit la ligne en commentaire.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Ajoutez ce qui suit à la ligne 105 pour utiliser une autre variante du composant et enregistrez le fichier. Appuyez sur **Ctrl + S** pour enregistrer le fichier.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/aem65-lab-code-update.png)

   Il est essentiel d’utiliser les majuscules correctes pour la variante « OutlinedInput » pour éviter l’échec de la compilation. La compilation de l’environnement de développement local commence automatiquement dans l’invite de commande. Patientez jusqu’à ce que le message suivant s’affiche.

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Actualisez le navigateur, s’il ne s’actualise pas automatiquement, pour voir le composant Entrée de texte utilisez une autre variante.

   ![](/help/assets/screenshot2028127729.png){width="50%" align="left"}


   Cette modification se produit pour les utilisatrices et utilisateurs finaux sans modification de la définition de formulaire sur le serveur AEM Forms et est spécifique
au canal découplé en cours de traitement. Par exemple, un canal web dans cet atelier.

   ![](/help/assets/aem65-lab-mui-style-update.png)


1. Fermez les fenêtres Visual Studio Code et Invite de commande.

## Questions fréquentes

+++ Les composants principaux sont-ils accessibles au public ?

Oui, les composants principaux de formulaires adaptatifs sont disponibles avec AEM Forms 6.5 et Forms as a Cloud Service. Vous avez besoin du pack de services 16 d’AEM Form  6.5 ou version ultérieure pour utiliser les composants principaux des formulaires adaptatifs.

+++

+++ Les formulaires découplés requièrent-ils une licence distincte ?

Non, les formulaires découplés utilisent la même mesure de valeur de licence et le même nombre d’envois de formulaire.

+++




## Étapes suivantes

Vous savez désormais comment créer des formulaires adaptatifs et les diffuser sur plusieurs canaux avec des formulaires découplés. Utilisez ces compétences pour créer des expériences de capture de données évolutives et de haute qualité, où que se trouvent vos utilisateurs.

## Ressources

* [Présentation des composants principaux des formulaires adaptatifs](https://experienceleague.adobe.com/fr/docs/experience-manager-core-components/using/adaptive-forms/introduction)

* [Création d’un formulaire adaptatif à l’aide des composants principaux](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components)

* [Mise à jour de la mise en forme pour le formulaire adaptatif basé sur les composants principaux](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components)

* [Formulaires adaptatifs découplés](https://experienceleague.adobe.com/fr/docs/experience-manager-headless-adaptive-forms/using/overview)

* [Utilisation d’un kit de démarrage Headless React](https://experienceleague.adobe.com/en/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form)
