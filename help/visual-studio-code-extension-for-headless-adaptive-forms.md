---
title: Extension Visual Studio Code pour les formulaires adaptatifs découplés
description: Extension Visual Studio Code pour les formulaires adaptatifs découplés
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: découplé, formulaires adaptatifs, extension Visual Studio Code
index: true
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
TQID: https://experienceleague.adobe.com/sf8qkVgbwMf2CGDsATHRYzq6idFQNFv3Os89oiCoiLU
product_v2: id: e8f6de9b-cf88-4405-8d10-15efa08c230eid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 12f711845becc93305717fb0c95e82355a8e97a5
workflow-type: tm+mt
source-wordcount: 231
ht-degree: 44%

---

# Extension Microsoft Visual Studio Code pour les formulaires adaptatifs découplés

Si vous utilisez ® Visual Studio Code en tant qu’IDE (environnement de développement intégré), vous pouvez utiliser l’extension Forms adaptative pour Microsoft Visual Studio Code. L’extension :

* Ajoute des fonctionnalités IntelliSense pour Adaptive Forms à Visual Studio Code.
* Permet de valider et de remplir automatiquement la syntaxe JSON pour les composants de formulaires adaptatifs découplés.
* Permet de parcourir facilement la structure d’un formulaire adaptatif découplé dans un panneau.
* Permet de traduire un formulaire adaptatif découplé.

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## Conditions préalables requises

* Téléchargez et installez [Microsoft Visual Studio Code 1.62.0 ou version ultérieure](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version). Si vous disposez d&#39;une ancienne version ou d&#39;aucune version installée, téléchargez la dernière version à partir du site Web de [](https://code.visualstudio.com/docs/setup/setup-overview). Pour utiliser Visual Studio à partir de la ligne de commande dans Apple macOS, consultez [Lancement à partir de la ligne de commande](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).
* Téléchargez l’[extension Adaptive Forms Builder](/help/assets/adaptive-form-builder-0.12.0.vsix).

## Installer l’extension

1. Ouvrez l’invite de commande et accédez au répertoire contenant le fichier d’extension téléchargé, *adaptive-form-builder-[version].vsix*.

1. Pour installer l’extension, exécutez la commande suivante :

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![Installation de l’extension](/help/assets/install-extension.png)


   Pour plus d’informations sur les fichiers .vsix, consultez l’[Aide de Microsoft Visual Studio Code](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace#_install-from-a-vsix).
