---
title: Problèmes connus du Forms adaptatif découplé
description: Problèmes connus des formulaires adaptatifs découplés.
keywords: découplé, formulaire adaptatif, problèmes connus
hide: true
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 53%

---


# Problèmes connus {#known-issues}

* Les modèles d’édition, d’affichage et de données ne sont pas pris en charge. (CQ-4327047)
* La contrainte minItems ne peut pas être modifiée de façon dynamique. (CQ-4342499)
* Les validations au niveau du panneau en cas de violation ne génèrent aucune erreur. (CQ-4342373)
* Les validations de fichiers en cas de violation ne génèrent aucune erreur. (CQ-4342372)
* Les propriétés personnalisées ne sont pas dynamiques. (CQ-4342376)
* La modification dynamique des données de fichier sur un événement de modification à l’aide d’expressions entraîne une boucle infinie. (CQ-4342377)
* La pièce jointe ne prend pas en charge le texte d’aide. (CQ-4342370)
* Si elle n’est pas cochée, la case obligatoire n’affiche pas d’erreur lors de l’envoi. (CQ-4342371)
* aria-label n&#39;est pas ajouté dans la pièce jointe. (CQ-4341494)
