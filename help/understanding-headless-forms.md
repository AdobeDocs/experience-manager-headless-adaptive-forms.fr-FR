---
title: Présentation des formulaires découplés - Concepts et FAQ
description: Réponses aux questions courantes sur ce que sont les formulaires découplés, en quoi ils diffèrent des bibliothèques de formulaires traditionnelles, détails d’implémentation, contrôle de l’interface utilisateur, performances et intégration aux structures et aux serveurs principaux.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: formulaires découplés, bibliothèque de formulaires découplés, formulaires adaptatifs, gestion des états, validation, système de conception, rendu côté serveur, CMS
hide: false
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '2605'
ht-degree: 5%

---


# Présentation des formulaires découplés - Concepts et FAQ {#understanding-headless-forms}

Ce guide répond aux questions courantes sur les formulaires découplés en général et leur application au Forms adaptatif découplé AEM. Utilisez-le pour décider quand utiliser une approche découplée et comment implémenter, mettre en forme et intégrer des formulaires dans votre pile.

## Principes de base et compréhension {#basics-understanding}

### Qu’est-ce qu’une bibliothèque de formulaires découplés ?

Une **bibliothèque de formulaires découplés** est une solution de formulaire qui sépare **logique de formulaire** (état, validation, règles, envoi) de **présentation** (composants de l’interface utilisateur et style). « head » est l’interface utilisateur des formulaires visibles ; « headless » signifie que la bibliothèque ne dicte pas ou n’envoie pas d’interface utilisateur fixe. Au lieu de cela, il expose :

* Un **modèle de formulaire** (souvent JSON) : structure, champs, contraintes et règles.
* **API ou hooks** pour lire et mettre à jour l’état du formulaire, exécuter une validation et gérer l’envoi.
* **Événements et cycle de vie** afin que votre interface utilisateur puisse réagir aux modifications.

Dans le Forms adaptatif découplé AEM, le formulaire est une structure [JSON](architecture.md) hébergée sur Adobe Experience Manager. [Forms Web SDK](architecture.md#developer-tools) (exécution côté client) fournit la couche logique (processeur de règles métier, gestion d’état, validation), tandis que votre application fournit l’interface utilisateur qui effectue le rendu de cette structure.

### En quoi un formulaire découplé est-il différent d’une bibliothèque de formulaires traditionnelle ?

| Aspect | Bibliothèque de formulaires traditionnelle | Bibliothèque de formulaires découplés |
|--------|---------------------------|------------------------|
| **UI** | Livré avec composants et styles intégrés | Pas d’IU prescrite ; vous apportez vos propres composants. |
| **Style** | Thème ou remplacements sur les composants de bibliothèque | Contrôle total ; utilisez votre système de conception tel quel |
| **Définition du formulaire** | Souvent en mode code uniquement (composants dans JSX/HTML) | Souvent piloté par des données (JSON/schéma de CMS ou API) |
| **État et validation** | Associé aux composants de bibliothèque | Exposé via des API/hooks ; toute interface utilisateur peut y être liée. |
| **Canaux** | Généralement web (parfois une structure) | La même définition de formulaire peut être utilisée pour le web, les appareils mobiles, le chat, etc. |

Avec le Forms adaptatif découplé AEM, vous [créez et publiez un formulaire](create-and-publish-a-headless-form.md) une fois dans AEM ; tout client (React, Angular, mobile natif, chatbot) peut [récupérer le formulaire JSON](architecture.md) et le rendre avec l’interface utilisateur appropriée pour ce canal.

### Pourquoi devrais-je utiliser des formulaires découplés au lieu d’une solution de formulaires basée sur l’interface utilisateur ?

Les formulaires découplés s’adaptent parfaitement à vos besoins :

* **Concevoir la cohérence du système** - Utilisez vos composants et votre marque existants sans combattre les paramètres par défaut de la bibliothèque.
* **Multicanal** - Une définition de formulaire pour le web, le mobile et d’autres points de contact (voir [Présentation](overview.md)).
* **Formulaires pilotés par CMS ou le serveur principal** - Les auteurs modifient la structure des formulaires et des règles sans déployer de code ; votre application utilise simplement le JSON.
* **Flexibilité du framework** - La bibliothèque [AF-core](https://www.npmjs.com/package/@aemforms/af-core) est indépendante du framework. Les liaisons React sont fournies pour des raisons pratiques, mais vous pouvez créer des liaisons pour d’autres frameworks.
* **Fonctionnalités du serveur principal** - Tirez parti d’AEM Forms pour le préremplissage, la validation, l’envoi, les workflows et le modèle de données Forms sans se verrouiller sur une pile d’interface utilisateur spécifique.

### À quel moment est-il logique d’utiliser une approche découplée ?

Utilisez des formulaires découplés lorsque :

* Vous disposez ou souhaitez disposer d&#39;un système de conception ou d&#39;une bibliothèque de composants performants.
* Les Forms sont créées par des non-développeurs (par exemple, dans un CMS) et doivent fonctionner sur plusieurs applications ou canaux.
* Vous avez besoin de la même logique de formulaire (validation, règles) pour les clients web, mobiles ou autres.
* Vous souhaitez minimiser les nouveaux rendus et conserver la logique de formulaire testable indépendamment de l’interface utilisateur.

Prenons l’exemple d’une bibliothèque de formulaires traditionnelle incluse dans l’interface utilisateur lorsque :

* Vous avez besoin d’un formulaire de travail dans une seule application web rapidement et ne vous souciez pas de l’interface utilisateur personnalisée ou du multicanal.
* Votre équipe préfère définir les formulaires uniquement dans le code dans un framework.

### Le terme « découplé » est-il simplement utilisé à la mode ou résout-il de vrais problèmes ?

Il résout de vrais problèmes d&#39;architecture :

* **Séparation des préoccupations** - La structure du formulaire, les règles et la validation vivent dans les données et une couche logique ; la couche de l’interface utilisateur effectue uniquement le rendu et la distribution des actions des utilisateurs. Cela améliore la testabilité et la réutilisation.
* **Indépendance du canal** - Une définition de formulaire peut piloter différentes interfaces utilisateur (par exemple, React web, React Native, Angular ou voix). Les Forms adaptatives découplées AEM sont conçues pour cela : [création unique, diffusion sur React, les SPA, le web, les appareils mobiles, etc](overview.md).
* **Création sans code** - Les utilisateurs professionnels peuvent modifier les champs et les règles dans l’[éditeur de formulaire adaptatif](create-a-headless-adaptive-form.md) ; les développeurs n’ont pas besoin de procéder à un redéploiement pour les modifications de contenu.
* **Intégration avec les piles existantes** - Vous conservez votre système de conception, la gestion des états et le routage ; la couche découplée ne gère que l’état, la validation et l’envoi des formulaires.

## Mise en œuvre et questions techniques {#implementation-technical}

### Comment les formulaires découplés gèrent-ils l’état ?

Dans le Forms adaptatif découplé AEM, l’état est géré par le **SDK Web Forms** :

* **Processeur de règles métier** - Accepte le JSON du formulaire, gère l’état des champs et exécute les règles et les gestionnaires d’événements définis dans le JSON.
* **Lieur React** - Fournit des points d’extension (par exemple, `useRuleEngine`) sur le contrôleur afin que les composants React reçoivent l’état et les gestionnaires actuels. Le même état peut être utilisé par les interfaces utilisateur autres que React via les API principales.
* **État** inclut les valeurs de champ, la visibilité, la validité et toutes les propriétés personnalisées définies dans le modèle de formulaire.

Vos composants d’interface utilisateur reçoivent l’état et les gestionnaires (par exemple, `[state, handlers] = useRuleEngine(props)`) ; vous effectuez le rendu à partir de `state` et appelez `handlers` lorsque l’utilisateur interagit. L’exécution conserve le statut synchronisé avec la définition et les règles de formulaire. Voir [Architecture](architecture.md) et [Utiliser des composants personnalisés pour effectuer le rendu d’un formulaire découplé](developing-for-headless-forms-using-your-own-components.md).

### Comment la validation fonctionne-t-elle dans une configuration de formulaire découplé ?

La validation fait partie de la couche logique du formulaire :

* Les **Contraintes** sont définies au format JSON (par exemple, obligatoire, min/max, modèle). Le SDK Web Forms applique ces contraintes et expose le statut de validation (par exemple, messages d’erreur valides/non valides) à vos composants.
* La **validation côté client** est appliquée par le SDK en fonction de la structure du formulaire ; votre interface utilisateur affiche les erreurs liées à l’état.
* La **validation côté serveur** est disponible via les API AEM (par exemple, valider le point d’entrée) ; vous pouvez la valider avant ou pendant l’envoi.

Vous n’implémentez pas de logique de validation dans votre interface utilisateur : vous affichez uniquement l’état et les messages de validation fournis par le runtime.

### Puis-je intégrer des formulaires découplés à la validation des schémas (Yup, Zod, Joi) ?

La validation intégrée est pilotée par les contraintes JSON du formulaire. Pour utiliser Yup, Zod, Joi ou similaire :

* Vous pouvez **dériver ou générer** le fichier JSON de formulaire adaptatif découplé à partir de votre schéma (par exemple, convertir le schéma JSON en formulaire JSON) afin qu’une source de vérité oriente à la fois la validation du schéma et la structure du formulaire.
* Pour la **validation personnalisée** au-delà du JSON du formulaire, vous pouvez exécuter vos propres validateurs (Yup/Zod/Joi) dans les gestionnaires d’événements ou avant l’envoi, et pousser les résultats vers l’état du formulaire ou bloquer l’envoi. Les points d’intégration sont les mêmes hooks/API que vous utilisez pour l’état et l’envoi.

Les [Spécification de Forms adaptatif](/help/assets/headless-adaptive-forms-specification.pdf) et [Formule JSON](architecture.md) définissent la règle et le modèle de contrainte utilisés par le runtime.

### Comment gérer la validation asynchrone (par exemple, disponibilité du nom d’utilisateur) ?

La validation asynchrone peut être implémentée dans votre couche d’application :

* Utilisez des **règles ou gestionnaires d’événements** dans le formulaire JSON (lorsqu’il est pris en charge) pour déclencher une logique lorsqu’un champ est modifié.
* Dans vos **composants personnalisés**, utilisez les mêmes hooks d’état/de gestionnaire pour appeler votre serveur principal (par exemple, l’API de disponibilité du nom d’utilisateur), puis mettez à jour la validité du champ ou affichez une erreur via les API d’exécution ou l’état local que vous faites apparaître dans l’interface utilisateur.
* Vous pouvez également effectuer la vérification **sur flou ou avant l’envoi** et définir l’état du champ sur non valide avec un message personnalisé si la vérification asynchrone échoue.

Le modèle exact dépend de la manière dont votre application s’intègre au [processeur de règles métier](architecture.md) et aux composants personnalisés.

### Comment envoyer des données aux API à l’aide de formulaires découplés ?

L’envoi est découplé de l’interface utilisateur :

* **Actions d’envoi AEM** - Configurez le formulaire dans AEM pour l’envoi aux points d’entrée REST, aux e-mails ou aux intégrations (par exemple, Microsoft Dynamics, Salesforce). Le formulaire est envoyé via AEM, qui gère l’appel HTTP/principal réel. Voir [&#x200B; Utilisation d’événements pour gérer et envoyer des données de formulaire](use-events-to-handle-and-submit-form-data.md).
* **Envoi côté client** - Votre application peut écouter l’envoi ou collecter des données de formulaire à partir de l’état d’exécution et les envoyer à vos propres API. Les [API HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) documentent la liste, la récupération, la validation, l’envoi et le suivi du statut d’envoi.
* **Préremplissage** - Les données peuvent être préremplies via des points d’entrée REST ou côté serveur, de sorte que lorsque le formulaire se charge, l’état est déjà renseigné. Voir [Storybook - exemple de préremplissage](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data).

## Contrôle de l’interface utilisateur et de la conception {#ui-design-control}

### Puis-je utiliser mon propre système de conception ou ma propre bibliothèque de composants avec des formulaires découplés ?

Oui. Il s’agit de l’un des principaux avantages des formulaires découplés. Avec le Forms adaptatif découplé AEM :

* Vous **mappez** vos propres composants au modèle de formulaire (par type de champ ou de ressource). Voir [Utilisation de composants personnalisés pour le rendu d’un formulaire découplé](developing-for-headless-forms-using-your-own-components.md) et [Utilisation des composants React de l’interface utilisateur Material Google pour le rendu d’un formulaire découplé](use-google-material-ui-react-components-to-render-a-headless-form.md).
* L’exécution fournit **état et gestionnaires** ; vos composants s’affichent à l’aide de votre système de conception et appellent les gestionnaires afin que la logique du formulaire reste synchronisée.
* Vous pouvez utiliser **le spectre React**, l’interface utilisateur Material, l’interface utilisateur Chakra ou toute bibliothèque de composants personnalisée ; la [spécification](/help/assets/headless-adaptive-forms-specification.pdf) peut être étendue pour les composants personnalisés (par exemple, l’interface utilisateur Chakra, Vue.js). Voir [FAQ - frameworks personnalisés](faq.md#is-it-possible-to-use-headless-adaptive-forms-with-custom-frameworks).

### Les formulaires découplés prennent-ils en charge l’accessibilité (ARIA, gestion du clavier) ?

L’accessibilité est implémentée dans le calque **UI** que vous fournissez. Le calque découplé n’effectue pas le rendu de DOM, de sorte qu’il n’ajoute pas le comportement ARIA ou clavier en lui-même. Pour obtenir l’accessibilité, procédez comme suit :

* Utilisation de **composants accessibles** à partir de votre système ou bibliothèque de conception (la plupart prennent en charge ARIA et le clavier).
* En suivant les **bonnes pratiques d’accessibilité** dans vos composants de champ personnalisés (libellés, messages d’erreur, gestion de la sélection, navigation au clavier).
* Assurez-vous que la structure et l’état de formulaire que vous recevez (par exemple, obligatoire, non valide, visible) sont reflétés dans les attributs ARIA et le comportement de vos composants.

Si vous utilisez les composants prêts à l’emploi basés sur le spectre React, vous bénéficiez de leur accessibilité intégrée.

### Comment gérer les composants complexes de l’interface utilisateur (sélecteurs de date, listes déroulantes personnalisées) ?

Traitez-les comme des **composants personnalisés** mappés aux types de champs correspondants ou aux types de ressources personnalisées dans le formulaire JSON :

* Mettez en œuvre votre composant pour accepter les mêmes **props/state/handlers** que les autres composants de champ (par exemple, via `useRuleEngine`).
* Utilisez **state** pour la valeur, la visibilité et la validité ; utilisez **handlers** pour mettre à jour la valeur et déclencher la validation.
* Effectuez le rendu de votre sélecteur de date ou de votre liste déroulante personnalisée avec la bibliothèque d’interface utilisateur de votre choix ; lors de la modification, appelez le gestionnaire avec la nouvelle valeur afin que l’état du formulaire reste correct.

Consultez [Utilisation de composants personnalisés pour le rendu d’un formulaire découplé](developing-for-headless-forms-using-your-own-components.md) pour le mappage par type de champ et type de ressource.

### Puis-je ajouter ou supprimer des champs de manière dynamique (formulaires dynamiques) ?

La structure du formulaire est définie par le **formulaire JSON** renvoyé par le serveur. Pour obtenir un comportement dynamique, procédez comme suit :

* **Règles dans le formulaire JSON** - Afficher/masquer, activer/désactiver ou définir des valeurs en fonction des expressions. Le [processeur de règles métier](architecture.md) exécute ces règles ; vos composants réagissent aux `state.visible` et à d’autres éléments similaires.
* **Structure pilotée par le serveur** - Différents utilisateurs ou contextes peuvent recevoir différents formulaires JSON (par exemple, différentes étapes ou sections). De ce fait, « dynamique » peut signifier « définition de formulaire différente par requête ».
* **Modifications côté client** - Si votre application peut modifier le modèle de formulaire (par exemple, ajouter/supprimer des éléments dans une structure répétable), l’exécution peut le refléter. La fonctionnalité exacte dépend du schéma de formulaire et des API d’exécution.

Le [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) comprend des exemples de comportement dynamique.

### Comment gérer les champs conditionnels (afficher/masquer en fonction de l’entrée) ?

La visibilité conditionnelle est pilotée par des **règles** au format JSON, évaluées par le processeur de règles métier. Vous définissez des conditions (par exemple, « lorsque le champ A est égal à X, afficher le champ B ») ; le runtime met à jour l’état (par exemple, `state.visible`). Vos composants doivent uniquement **respecter l’état** (par exemple, `if (!state.visible) return null;`). Aucune logique d’interface utilisateur supplémentaire n’est requise pour afficher/masquer au-delà du rendu à partir de l’état. Le comportement en cascade et conditionnel est documenté dans la [Spécification de Forms adaptatif](/help/assets/headless-adaptive-forms-specification.pdf) et démontré dans [Storybook - champs en cascade](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down). Voir aussi [FAQ - champs en cascade](faq.md#do-headless-adaptive-forms-support-cascading-fields).

## Performances et évolutivité {#performance-scalability}

### Les formulaires découplés sont-ils plus performants que les bibliothèques de formulaires traditionnelles ?

Elles peuvent l’être, mais cela dépend de l’implémentation :

* **Mises à jour ciblées** - Une exécution découplée bien conçue ne met à jour que l’état qui a changé et ne notifie que les composants qui en dépendent, ce qui peut réduire les nouveaux rendus inutiles par rapport à un composant de formulaire monolithique.
* **Offre groupée d’IU plus petite** - Vous n’envoyez que les composants d’IU que vous utilisez (votre système de conception), et non un ensemble complet de composants de bibliothèque.
* **Chargement différé** - Le formulaire JSON peut être récupéré si nécessaire ; le lot initial peut rester plus petit.

Les performances dépendent également de la manière dont vous implémentez vos composants (par exemple, en évitant les nouveaux rendus inutiles, la mémorisation).

### Comment réduisent-ils les nouveaux rendus ?

* **Forme d’état** - L’exécution conserve l’état du formulaire dans une structure qui permet des mises à jour affinées afin que seules les parties affectées de l’arborescence aient besoin d’effectuer un nouveau rendu.
* **Conception de hooks** - Des hooks tels que `useRuleEngine` peuvent être implémentés pour abonner les composants uniquement au statut qu’ils utilisent, de sorte que les modifications du parent ou du frère ne forcent pas chaque champ à effectuer un nouveau rendu.
* **Votre responsabilité** - Vous pouvez réduire davantage les nouveaux rendus en utilisant les bonnes pratiques React (par exemple, `React.memo`, rappels stables) dans vos composants personnalisés.

### Les formulaires découplés sont-ils adaptés aux formulaires volumineux à plusieurs étapes ?

Oui, lorsqu’elle est conçue de manière appropriée :

* **Définition du formulaire** - Les formulaires volumineux peuvent être divisés en étapes ou en sections dans le fichier JSON. Seules les étapes/sections visibles peuvent être entièrement actives dans l’interface utilisateur, avec une évaluation différée des règles pour les sections masquées si elle est prise en charge.
* **State** - L’exécution contient un état de formulaire cohérent ; la navigation par étapes affiche/masque simplement des sections ou met à jour « l’étape actuelle » sans dupliquer les données.
* **Fragmentation et chargement différé** - Vous pouvez récupérer des fichiers JSON par blocs ou charger des sections supplémentaires à l’avance pour réduire la charge utile initiale et les coûts d’analyse.

Pour les formulaires très volumineux, tenez compte de la structure (par exemple, les étapes de l’assistant), des variantes de formulaire pilotées par le serveur et de la mesure de l’exécution du rendu et des règles avec des payloads réels.

## Intégration et écosystème {#integration-ecosystem}

### Les formulaires découplés peuvent-ils fonctionner avec les actions Next.js / SSR / serveur ?

* **Next.js / React** - Oui. Le rendu et les points d’extension React fonctionnent dans un environnement React. Utiliser le SDK Web Forms dans les composants clients ; récupérer les fichiers JSON sur le serveur ou le client selon les besoins.
* **SSR** - Vous pouvez récupérer le fichier JSON du formulaire sur le serveur et le transmettre au client afin que le formulaire s’hydrate avec les données. L’interactivité du formulaire (état, validation, règles) s’exécute sur le client sur lequel le SDK est chargé. Évitez de rendre des champs de formulaire qui dépendent d’un état client uniquement lors du rendu côté serveur ou utilisez un espace réservé qui s’hydrate sur le client.
* **Actions du serveur (Next.js)** - Vous pouvez appeler des actions du serveur à partir de votre gestionnaire d’envoi : lorsque l’utilisateur effectue un envoi, votre code client collecte des données de formulaire (à partir de l’état découplé) et appelle une action du serveur à la place ou en plus des points d’entrée d’envoi AEM.

### Comment les formulaires découplés s’intègrent-ils à CMS, au commerce découplé ou aux systèmes back-end ?

* **CMS** - AEM est le CMS de la définition du formulaire : les auteurs créent et publient le fichier JSON du formulaire. D’autres CMS peuvent référencer ou lier l’URL/l’API du formulaire. Votre application récupère le formulaire à partir d’AEM (ou d’un réseau CDN) et extrait éventuellement une copie ou une mise en page d’un autre CMS.
* **Préremplissage et envoi** - Le [préremplissage](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) et l’envoi peuvent atteindre les points d’entrée REST. Vous pouvez donc préremplir à partir d’un serveur principal CRM, DAM ou Commerce et envoyer l’envoi aux mêmes systèmes ou à des systèmes différents. AEM Forms prend également en charge [Microsoft Dynamics et Salesforce](faq.md), REST, les e-mails et les actions d’envoi personnalisées.
* **Modèle de données Forms** - AEM Forms fournit un modèle de données Forms pour se connecter à des sources de données disparates ; les formulaires découplés peuvent utiliser ces fonctionnalités pour le préremplissage, la validation et l’envoi sans que vous ayez à créer vous-même chaque intégration.

Pour les scénarios mobiles et hors ligne, l’approche recommandée est de [créer votre propre application et récupérer les définitions de formulaire via l’API de Forms adaptative découplée](mobile-forms-best-practices.md).

## Voir également {#see-also}

* [Vue d’ensemble](overview.md)
* [Architecture](architecture.md)
* [Questions fréquentes](faq.md)
* [Créer et publier un formulaire découplé](create-and-publish-a-headless-form.md)
* [API de formulaires adaptatifs découplés](https://opensource.adobe.com/aem-forms-af-runtime/api/)
* [Terrain de jeu de code](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=fr)
* [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)
