---
title: Utilisation de composants personnalisés pour effectuer le rendu d’un formulaire découplé
description: Découvrez comment créer des composants personnalisés et les mapper à des champs de Forms adaptatif découplé. Ce guide explique comment mapper des composants par type de champ et type de ressource pour obtenir un rendu et un comportement personnalisés.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: 5aba1821-35dc-4da4-b188-d4853d64d5ee
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Utilisation de composants personnalisés pour effectuer le rendu d’un formulaire découplé {#developing-for-headless-forms-using-your-own-components}

Dans le Forms adaptatif découplé, vous pouvez créer et implémenter des composants personnalisés pour définir l’aspect et les fonctionnalités de vos formulaires. Bien que les composants par défaut fournissent un comportement standard, vous aurez peut-être besoin d’éléments ou d’interactions d’interface utilisateur spécifiques, tels qu’un composant « Annonce » personnalisé ou un champ « Signature tactile » spécialisé.

Cet article vous guide tout au long de la création d’un composant React personnalisé et de son mappage à votre formulaire adaptatif découplé.

## &#x200B;1. Créer un composant React personnalisé

Créez tout d’abord le composant React qui effectuera le rendu de votre champ de formulaire. Ce composant peut utiliser n’importe quelle bibliothèque React (comme l’interface utilisateur Material, Ant Design ou vos propres styles personnalisés).

Par exemple, nous allons créer un composant personnalisé **Annonce** qui effectue le rendu d’un message en lecture seule avec un style spécifique.

1. Accédez au répertoire des composants de votre projet React (par exemple, `src/components`).
2. Créez un dossier et un fichier pour votre composant, par exemple `Announcement/index.tsx`.
3. Mettez en œuvre le composant . Il doit accepter des `props` compatibles avec l’exécution Forms découplée (recevant généralement l’état du champ ).

```tsx
import React from 'react';
import { useRuleEngine } from '@aemforms/af-react-renderer';
import { FieldJson, State } from '@aemforms/af-core';

const Announcement = function (props: State<FieldJson>) {
    // The useRuleEngine hook connects the component to the form logic
    const [state, handlers] = useRuleEngine(props);

    if (!state.visible) {
        return null;
    }

    return (
        <div className="custom-announcement" style={{ border: '1px solid #ccc', padding: '10px', backgroundColor: '#f9f9f9' }}>
            <h3>{state?.label?.value}</h3>
            <p>{state?.default}</p>
        </div>
    );
}

export default Announcement;
```

## &#x200B;2. Mapper le composant personnalisé

Pour utiliser votre composant personnalisé, vous devez le mapper dans le fichier `mappings.ts`. L’exécution du Forms découplé utilise ce mappage pour déterminer le composant React à afficher pour chaque champ du formulaire JSON.

Il existe deux méthodes principales pour mapper des composants : par **Type de champ** ou par **Type de ressource**.

### Mappage par type de champ

Le mappage standard est basé sur la propriété `fieldType` dans le JSON du formulaire (par exemple, `text-input`, `checkbox`, `button`). Cela s’avère utile lorsque vous souhaitez remplacer *toutes* les instances d’un composant standard par votre version personnalisée.

1. Ouvrez `src/utils/mappings.ts` (ou à l’endroit où vos mappages sont définis).
2. Importez votre composant personnalisé.
3. Ajoutez-le à l’objet de mappages à l’aide de l’`fieldType` comme clé.

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  "text-input": Announcement // This would replace ALL text-input fields (use with caution)
};

export default customMappings;
```

### Mappage par type de ressource (composants personnalisés)

Si vous avez créé un composant personnalisé dans AEM (par exemple, un composant « Annonce » étendant un composant Texte standard) et que vous souhaitez effectuer le rendu *uniquement* de ce composant spécifique différemment dans votre application React, vous devez le mapper par son **Type de ressource** ou un identifiant unique.

Cette approche vous permet de générer normalement les composants de texte standard, tandis que votre composant « Annonce » personnalisé utilise votre implémentation React spécialisée.

1. Identifiez l’identifiant unique de votre composant. Dans le JSON de formulaire découplé, cette fonctionnalité est souvent présente dans la propriété `:type` ou dans un `fieldType` personnalisé s’il est configuré.
2. Ajoutez le mappage à l’aide de cet identifiant.

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  // Map by resource type or custom identifier
  "my-project/components/announcement": Announcement
};

export default customMappings;
```

> **Remarque :** assurez-vous que votre modèle de formulaire AEM exporte le `:type` ou l’identifiant correct correspondant à la clé que vous utilisez dans `mappings.ts`.

## &#x200B;3. Application des mappages

Enfin, assurez-vous que votre instance de formulaire découplé utilise ces mappages personnalisés.

```tsx
import React from 'react';
import { AdaptiveForm } from '@aemforms/af-react-renderer';
import customMappings from './utils/mappings';
import formJSON from './form-def.json';

function App() {
  return (
    <AdaptiveForm
      formJson={formJSON}
      mappings={customMappings}
    />
  );
}

export default App;
```

En suivant ces étapes, vous pouvez étendre les fonctionnalités de votre Forms adaptative découplée avec des composants qui correspondent à vos exigences fonctionnelles et de conception spécifiques.
