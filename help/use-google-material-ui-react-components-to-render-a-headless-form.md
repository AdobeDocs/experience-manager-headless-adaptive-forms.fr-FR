---
title: Utiliser les composants React de l’interface utilisateur Material de Google pour effectuer le rendu d’un formulaire découplé
description: Découvrez comment utiliser les composants React de l’interface utilisateur Material de Google pour générer un formulaire découplé. Ce guide complet vous guide tout au long du processus détaillé de création de composants Forms adaptatifs découplés personnalisés pour mapper et utiliser les composants React Material-UI de Google pour appliquer un style à un formulaire adaptatif découplé.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: 476509d5-f4c1-4d1c-b124-4c278f67b1ef
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 51%

---


# Utiliser une bibliothèque React personnalisée pour afficher un formulaire découplé

<!-- This article is completely missing the image ALT tags (descriptions) for each added image asset. That is impacting the CQI score for Experience Manager in a negative way. Be sure you add the required missing image ALT tags.  -->

Vous pouvez créer et implémenter des composants personnalisés pour personnaliser l’apparence et les fonctionnalités (comportement) de vos formulaires adaptatifs découplés conformément aux exigences et directives de votre entreprise.

Ces composants ont deux objectifs principaux : contrôler l’aspect ou le style des champs des formulaires et stocker les données collectées à travers ces champs dans l’instance de modèle des formulaires. Si cela semble déroutant, ne vous inquiétez pas : vous allez bientôt explorer ces objectifs plus en détail. Pour l’instant, concentrons-nous sur les premières étapes de création de composants personnalisés, de rendu du formulaire à l’aide de ces composants et d’utilisation d’événements pour enregistrer et envoyer des données à un point d’entrée REST.

Dans ce tutoriel, les composants de l’interface utilisateur Material Google sont utilisés pour démontrer comment effectuer le rendu d’un formulaire adaptatif découplé à l’aide de composants React personnalisés. Cependant, vous n’êtes pas limité à cette bibliothèque et vous êtes libre d’utiliser n’importe quelle bibliothèque de composants React ou de développer vos propres composants personnalisés.

À la fin de cet article, l’article _Nous contacter_ créé dans [Créer et publier un formulaire découplé à l’aide du kit de démarrage](create-and-publish-a-headless-form.md) se transforme en ce qui suit :

![](assets/headless-adaptive-form-with-google-material-ui-components.png)


Les principales étapes nécessaires à l’utilisation des composants de l’interface utilisateur Material de Google pour générer un formulaire sont les suivantes :

![](assets/headless-forms-graphics-source-main.svg)

## &#x200B;1. Installer l’interface utilisateur Material de Google

Par défaut, le kit de démarrage utilise les composants d’[Adobe Spectrum](https://spectrum.adobe.com/). Commençons par la configuration pour utiliser l’[interface utilisateur Material de Google](https://mui.com/) :

1. Assurez-vous que le kit de démarrage n’est pas en cours d’exécution. Pour arrêter le kit de démarrage, ouvrez votre terminal, accédez au **react-starter-kit-aem-headless-forms**, puis appuyez sur Ctrl-C (il en est de même sous Windows, Mac et Linux®).

   Ne tentez pas de fermer le terminal. La fermeture de votre terminal n’arrête pas le kit de démarrage.

1. Exécutez la commande suivante :

```shell
    
    npm install @mui/material @emotion/react @emotion/styled --force
    
```

Celle-ci installe les bibliothèques npm de l’interface utilisateur Material de Google et ajoute les bibliothèques aux dépendances des kits de démarrage. Vous pouvez désormais utiliser les composants de l’interface utilisateur Material pour effectuer le rendu des composants de formulaire.


## &#x200B;2. Créer des composants React personnalisés

Créons un composant personnalisé qui remplace le composant par défaut [entrée de texte](https://spectrum.adobe.com/page/text-field/) par le composant [Champ de texte de l’interface utilisateur Material Google](https://mui.com/material-ui/react-text-field/).

Un composant distinct est requis pour chaque type de composant ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input) ou `:type`) utilisé dans une définition de formulaire découplé. Par exemple, dans le formulaire de contact que vous avez créé dans la section précédente, les champs Nom, Adresse e-mail et Téléphone sont de type `text-input` ([fieldType: &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def)) et le champ du message est de type `multiline-input` ([&quot;fieldType&quot;: &quot;multiline-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/reference-json-properties-fieldtype--multiline-input)).


Créons un composant personnalisé pour superposer tous les champs de formulaire qui utilisent la propriété [fieldType: « text-input »](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def) avec le composant [Material UI Text Field](https://mui.com/material-ui/react-text-field/).


Pour créer et mapper un composant personnalisé avec la propriété [fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def) :

1. Ouvrez le répertoire **react-starter-kit-aem-headless-forms** dans un éditeur de code et accédez à `\react-starter-kit-aem-headless-forms\src\components`.


1. Créez une copie du dossier **`slider`** ou **`richtext`**, puis renommez le dossier copié en **materialtextfield**. Le `slider` et le `richtext` sont deux exemples de composants personnalisés disponibles dans l’application de démarrage. Vous pouvez utiliser ces composants pour créer vos propres composants personnalisés.

   ![Le composant personnalisé materialtextfield dans VSCode](/help/assets/richtext-custom-component-in-vscode.png)

1. Ouvrez le fichier `\react-starter-kit-aem-headless-forms\src\components\materialtextfield\index.tsx` et remplacez le code existant par le code ci-dessous. Ce code renvoie et produit un composant de [champ de texte Interface utilisateur Material de Google](https://mui.com/material-ui/react-text-field/).

```JavaScript
 
     import React from 'react';
     import {useRuleEngine} from '@aemforms/af-react-renderer';
     import {FieldJson, State} from '@aemforms/af-core';
     import { TextField } from '@mui/material';
     import Box from '@mui/material/Box';
     import { richTextString } from '@aemforms/af-react-components';
     import Typography from '@mui/material/Typography';


     const MaterialtextField = function (props: State<FieldJson>) {

         const [state, handlers] = useRuleEngine(props);

         return(

         <Box>
             <Typography component="legend">{state.visible ? richTextString(state?.label?.value): ""} </Typography>
             <TextField variant="filled"/>
         </Box>

         )
     }

     export default MaterialtextField;
```


La partie `state.visible` vérifie si le composant est défini comme étant visible. Si tel est le cas, le libellé du champ est récupéré et affiché à l’aide de `richTextString(state?.label?.value)`.

![](/help/assets/material-text-field.png)


Votre composant personnalisé `materialtextfield` est prêt. Définissons ce composant personnalisé afin qu’il remplace toutes les instances de [fieldType: &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def) par le Champ de texte Interface utilisateur Material de Google.

## &#x200B;3. Mapper un composant personnalisé avec des champs de formulaire découplés

Le processus d’utilisation de composants de bibliothèque tiers pour effectuer le rendu des champs de formulaire est connu sous le nom de mappage. Vous mappez chaque ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input)) à un composant correspondant d’une bibliothèque tierce.

Toutes les informations relatives au mappage sont ajoutées au fichier `mappings.ts`. L’instruction `...mappings` dans le fichier `mappings.ts` fait référence aux mappages par défaut, qui superposent les composants ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input) ou `:type`) avec [Adobe Spectrum](https://spectrum.adobe.com/page/text-field/).

Pour ajouter un mappage pour le composant `materialtextfield`, créé à la dernière étape :

1. Ouvrez le fichier `mappings.ts`.

1. Ajoutez l’instruction d’import suivante pour inclure le composant `materialtextfield` au fichier `mappings.ts` :


   ```JavaScript
       import MaterialtextField from "../components/materialtextfield";
   ```

1. Ajoutez l’instruction suivante pour mapper `text-input` avec le composant materialtextfield.


   ```JavaScript
       "text-input": MaterialtextField
   ```

   Le code final du fichier ressemble à ce qui suit :

   ```JavaScript
         import { mappings } from "@aemforms/af-react-components";
         import MaterialtextField from "../components/materialtextfield";
   
   
         const customMappings: any = {
           ...mappings,
           "text-input": MaterialtextField
        };
        export default customMappings;
   ```

1. Enregistrez l’application, puis exécutez-la. Les trois premiers champs du formulaire sont rendus à l’aide du [champ de texte Interface utilisateur Material de Google](https://mui.com/material-ui/react-text-field/) :

   ![](assets/material-text-field-form-rendetion.png)


   De même, vous pouvez créer des composants personnalisés pour le message (« fieldType »: « multiline-input ») et évaluer les champs de service (« fieldType »:« number-input »). Vous pouvez cloner le référentiel Git suivant pour les composants personnalisés du message et évaluer les champs de service :

   [https://github.com/singhkh/react-starter-kit-aem-headless-forms](https://github.com/singhkh/react-starter-kit-aem-headless-forms)

## Étape suivante

Vous avez réussi à rendre le formulaire avec des composants personnalisés qui utilisent l’interface utilisateur Material de Google. Avez-vous essayé d’envoyer le formulaire en cliquant sur le bouton Envoyer (associé au composant correspondant de l’interface utilisateur Material Google) ? Si ce n&#39;est pas le cas, allez-y, essayez.

Le formulaire envoie-t-il les données à une source de données ? Non ? Ne vous inquiétez pas. En effet, votre formulaire n’est pas configuré pour communiquer avec la bibliothèque d’exécution.

Comment configurer votre formulaire pour communiquer avec elle ? Un article va bientôt vous expliquer tout en détail. Restez à l’écoute !
