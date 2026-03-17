---
title: Uso de componentes personalizados para procesar un formulario sin encabezado
description: Aprenda a crear componentes personalizados y asignarlos a campos de Forms adaptables sin encabezado. Esta guía explica cómo asignar componentes por tipo de campo y tipo de recurso para lograr un procesamiento y un comportamiento personalizados.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
index: true
exl-id: 5aba1821-35dc-4da4-b188-d4853d64d5ee
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Uso de componentes personalizados para procesar un formulario sin encabezado {#developing-for-headless-forms-using-your-own-components}

En Forms adaptable sin encabezado, puede crear e implementar componentes personalizados para definir el aspecto y la funcionalidad de los formularios. Aunque los componentes predeterminados proporcionan un comportamiento estándar, es posible que necesite elementos de interfaz de usuario o interacciones específicos, como un componente &quot;Anuncio&quot; personalizado o un campo especializado en &quot;Firma manuscrita&quot;.

Este artículo le guía a través de la creación de un componente React personalizado y su asignación a su formulario adaptable sin encabezado.

## &#x200B;1. Crear un componente React personalizado

Primero, cree el componente React que procesará el campo de formulario. Este componente puede utilizar cualquier biblioteca de React (como Material UI, Ant Design o sus propios estilos personalizados).

Por ejemplo, vamos a crear un componente **Anuncio** personalizado que procese un mensaje de solo lectura con un estilo específico.

1. Vaya al directorio de componentes del proyecto de React (por ejemplo, `src/components`).
2. Cree una carpeta y un archivo nuevos para el componente, por ejemplo `Announcement/index.tsx`.
3. Implemente el componente. Debe aceptar `props` compatible con el tiempo de ejecución de Forms sin encabezado (que generalmente recibe el estado del campo).

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

## &#x200B;2. Asignación del componente personalizado

Para utilizar el componente personalizado, debe asignarlo en el archivo `mappings.ts`. El tiempo de ejecución de Forms sin encabezado utiliza esta asignación para determinar qué componente de React se procesará para cada campo del formulario JSON.

Existen dos formas principales de asignar componentes: por **Tipo de campo** o por **Tipo de recurso**.

### Asignación por tipo de campo

La asignación estándar se basa en la propiedad `fieldType` del formulario JSON (por ejemplo, `text-input`, `checkbox`, `button`). Esto es útil cuando desea reemplazar *todas* las instancias de un componente estándar con su versión personalizada.

1. Abra `src/utils/mappings.ts` (o donde quiera que estén definidas sus asignaciones).
2. Importe el componente personalizado.
3. Agréguelo al objeto de asignaciones usando `fieldType` como clave.

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  "text-input": Announcement // This would replace ALL text-input fields (use with caution)
};

export default customMappings;
```

### Asignación por tipo de recurso (componentes personalizados)

Si ha creado un componente personalizado en AEM (por ejemplo, un componente &quot;Anuncio&quot; que amplía un componente Texto estándar) y desea procesar *solo* ese componente específico de forma diferente en la aplicación React, debe asignarlo por su **Tipo de recurso** o un identificador único.

Este método permite procesar normalmente los componentes de texto estándar, mientras que el componente personalizado &quot;Anuncio&quot; utiliza la implementación React especializada.

1. Identifique el identificador único del componente. En el JSON del formulario sin encabezado, esto se encuentra a menudo en la propiedad `:type` o en un `fieldType` personalizado si está configurado.
2. Añada la asignación con este identificador.

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

> **Nota:** Asegúrese de que el modelo de formularios de AEM exporta el `:type` o identificador correcto que coincida con la clave que utiliza en `mappings.ts`.

## &#x200B;3. Aplicar las asignaciones

Finalmente, asegúrese de que la instancia de formulario sin encabezado utiliza estas asignaciones personalizadas.

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

Al seguir estos pasos, puede ampliar las capacidades de su Forms adaptable sin encabezado con componentes que se ajustan a sus requisitos funcionales y de diseño específicos.
