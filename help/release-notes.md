---
title: Información general sobre los formularios adaptables sin encabezado de AEM
description: Información general de los formularios adaptables sin encabezado de AEM.
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: ht
source-wordcount: '477'
ht-degree: 100%

---


# Notas de la versión

Le damos la bienvenida a la versión para principiantes de los formularios adaptables sin encabezado de Experience Manager. Continúe leyendo para conocer recursos e instrucciones para comenzar y aprovechar al máximo el lanzamiento.

Utilice los formularios adaptables sin encabezado de Adobe Experience Manager para crear aplicaciones de formularios con marcos de trabajo front-end, como React, Angular y otros. Utilice la SDK web de los formularios adaptables para la administración de estado, la validación y la integración con puntos de contacto adicionales.


La versión para principiantes le proporciona acceso para utilizar formularios adaptables sin encabezado en un [entorno de desarrollo local](setup-development-environment.md). Puede utilizar el entorno de desarrollo local para crear y probar formularios adaptables sin encabezado.

Los formularios adaptables sin encabezado reciben mejoras de forma continua. Para estar al día de los desarrollos más recientes, visite esta página regularmente. Esta página le suministra información sobre lo siguiente:

* acceso temprano
* últimas versiones
* nuevas funciones
* Mejoras
* correcciones de errores
* funcionalidad obsoleta
* instrucciones especiales
* Planes de futuros cambios

<!-- 

## July 2022 (v0.22.1)

### New features

* Introduced the `validateFormData` API. It validates all the components against the rules and constraints an returns the list of errors. The validation takes place on the server.
* Introduced the `FormLoad` event.
* Introduced the `importData` and `exportData`.
* You can now dynamically add or remove items, that expect unqiue values, from a repeatable panel. You can use the `minItems` and `maxitems` constraint to set limit of item.
* You can now use constraint to set maximum file upload size, accepted file types, minimum files, and maximum files to upload.

### Improvements and bug fixes

* The service was executing some event handlers twice. The issue is fixed.
* Fixing Data Generation with different values of dataRef, name and type.

<!-- ### React Renderer component -->

## Artefactos disponibles en la versión para principiantes

En el recorrido para ofrecerle los formularios adaptables sin encabezado de Adobe Experience Manager, los siguientes artefactos están disponibles en la versión para principiantes:

### SDK de AEM Forms as a Cloud Service

El SDK de AEM Forms as a Cloud Service para ayudarle a crear, almacenar y recuperar formularios adaptables sin encabezado. También proporciona servicios de rellenado previo, validación de reglas del lado del servidor y envío para formularios adaptables sin encabezado.

### SDK web de Forms

El SDK web de Forms proporciona las API para validar las restricciones aplicadas a varios campos de un formulario y enlaces para conectar la estructura JSON del formulario al marco de trabajo de la IU. También facilita el procesador React para formularios adaptables sin encabezado para ayudarle a integrarlos en su aplicación. Están disponibles los siguientes componentes del SDK web:

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### Storybook

El [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) proporciona información general sobre los diferentes componentes de los formularios adaptables sin encabezado. También proporciona una lista de todos los componentes admitidos, sus correspondientes propiedades y restricciones.

### Componente principal de Forms

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

Los componentes principales son un conjunto de componentes estandarizados de la gestión de contenidos web (WCM) que le ayudan a acelerar el tiempo de desarrollo y reducir el coste de mantenimiento de sus formularios. El componente Contenedor de Forms es el principal. Le ayuda a incrustar y procesar una estructura JSON de formulario adaptable sin encabezado en el editor de formularios adaptables del SDK de Forms as a Cloud Service.

### Especificaciones de formularios adaptables V2

La especificación de formularios adaptables sin encabezado proporciona información detallada sobre todos los componentes, restricciones y métodos disponibles para definir formularios adaptables sin encabezado. La especificación está disponible en formato [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf).

### API de HTTP y JS

Las [API de HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) le permiten enumerar, recuperar, validar, enviar y seguir el estado de envío de los formularios sin encabezado. <!-- URL is 404! [JS APIs](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) helps you use Headless adaptive forms with any JavaScript based UI framework. -->

### Extensión de código de Visual Studio

[Extensión de código de Visual Studio](visual-studio-code-extension-for-headless-adaptive-forms.md) para crear una estructura JSON válida. Proporciona soporte y validación de IntelliSense para la estructura JSON de formularios junto con funciones comunes como añadir, eliminar o cambiar el nombre de componentes de una estructura JSON.

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->