---
title: Preguntas frecuentes sobre los formularios adaptables sin encabezado
description: Preguntas frecuentes
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: sin encabezado, formulario adaptable, preguntas frecuentes
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 58%

---

# Preguntas frecuentes {#headless-adaptive-forms-faq}

## ¿Debo saber React.js para usar formularios adaptativos sin encabezado?

Puede usar cualquier marco de trabajo, biblioteca o lenguaje para procesar los formularios adaptables sin encabezado y utilizar las API REST de Adobe para validarlos y enviarlos. La biblioteca -core de AF, que se proporciona de forma predeterminada, es independiente del marco de trabajo. Las bibliotecas React-Render y React-Component, que también se suministran de forma predeterminada están pensadas para su comodidad. Puede desarrollar sus propios componentes y no tendrá que limitarse a los que se facilitan.


<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## ¿Necesito que la zona protegida de Forms as a Cloud Service utilice formularios adaptables sin encabezado?

Puede utilizar la aplicación de inicio para comenzar a desarrollar y diseñar sus formularios adaptables sin encabezado. Necesita Forms as a Cloud Service para alojar y ofrecer formularios adaptables sin encabezado junto con capacidades de formularios backend.

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## ¿Dónde puedo obtener una vista previa de un formulario adaptable sin encabezado? {#storybook-example}

Puede utilizar la aplicación de inicio para procesar y previsualizar un formulario adaptable sin encabezado personalizado. También puede modificar un ejemplo de [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) para previsualizar un formulario adaptable sin encabezado.

![](/help/assets/storybook-example.png)

## ¿Es posible usar formularios adaptables sin encabezado con marcos personalizados?

Los formularios adaptables sin encabezado se basan en la [especificación estándar](/help/assets/headless-adaptive-forms-specification.pdf). Puede ampliar la especificación para utilizarla para crear componentes personalizados. Por ejemplo, componentes para Chakra UI, Vue.js y más.

## ¿Los formularios adaptables sin encabezado admiten campos en cascada?

En los campos en cascada, el contenido del segundo campo depende del contenido elegido en el primero. [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down) proporciona un ejemplo de campos en cascada.

## ¿Los formularios adaptables sin encabezado permiten rellenar previamente los formularios con datos personalizados?

Los formularios adaptables sin encabezado permiten rellenar previamente formularios con datos personalizados. [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) proporciona un ejemplo de cómo rellenar previamente un formulario adaptable sin encabezado.

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## ¿Puedo utilizar formularios adaptables sin encabezado con la SPA de Angular?

Puede utilizar el SDK web para integrar formularios adaptables sin encabezado con la SPA de Angular. Es independiente de cualquier marco. Puede utilizar el SDK de React como referencia.

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## ¿Existe algún complemento para facilitar el desarrollo de formularios adaptables sin encabezado?

Sí, una extensión de Visual Studio Code le permite crear manualmente formularios adaptables sin encabezado en JSON.

## ¿Cuál es el enfoque recomendado para formularios móviles o sin conexión? {#mobile-offline-forms}

Cree su propia aplicación nativa y recupere definiciones de formularios a través de la API de Forms adaptable sin encabezado. Si lo desea, puede implementar la compatibilidad sin conexión (por ejemplo, almacenamiento local y sincronización). Consulte [Prácticas recomendadas de formularios móviles](mobile-forms-best-practices.md) para ver el método recomendado y los vínculos a las API.

## ¿Cómo se utilizan las API de GraphQL o sin encabezado con AEM Forms?

AEM sin encabezado para Forms adaptable usa **API HTTP/REST**, no GraphQL. La aplicación llama a estas API para enumerar formularios, obtener una definición de formulario (JSON), validar, enviar y rastrear el estado de envío. Use las [API HTTP de formularios adaptables sin encabezado](https://opensource.adobe.com/aem-forms-af-runtime/api/) para obtener la referencia completa. Para saber cómo se recuperan y procesan los formularios, consulte [Arquitectura](architecture.md) y [Explicación de los formularios sin encabezado](understanding-headless-forms.md).

## ¿Cómo puedo implementar y aplicar estilo a los formularios sin encabezado mediante los componentes de React en Adobe AEM Forms?

Implemente y aplique estilo a los formularios sin encabezado mediante sus propios componentes de React y CSS (o una biblioteca de interfaz de usuario como la interfaz de usuario de Material). La lógica de formulario (estado, validación y reglas) proviene de Forms Web SDK y del formulario JSON; su aplicación proporciona la interfaz de usuario que lo procesa.

* Para aplicar estilo a un formulario sin encabezado con una biblioteca de la interfaz de usuario de React, consulte [Usar una biblioteca de React personalizada para procesar un formulario sin encabezado](use-google-material-ui-react-components-to-render-a-headless-form.md).
* Para generar y asignar componentes de React personalizados a campos de formulario, consulte [Usar componentes personalizados para procesar un formulario sin encabezado](developing-for-headless-forms-using-your-own-components.md).

Para conocer conceptos como cuándo usar formularios sin encabezado, administración de estado y validación, consulte [Explicación de los formularios sin encabezado](understanding-headless-forms.md).

## ¿Cómo puedo implementar y personalizar AEM Forms con CSS, temáticas, editores de reglas y formularios sin encabezado personalizados?

**Formularios sin encabezado:** El estilo y el aspecto están totalmente bajo su control. Utiliza sus propios componentes de React (u otros) y su propio CSS; no hay temáticas integradas. Vea [Usar una biblioteca de React personalizada para procesar un formulario sin encabezado](use-google-material-ui-react-components-to-render-a-headless-form.md) y [Usar componentes personalizados para procesar un formulario sin encabezado](developing-for-headless-forms-using-your-own-components.md) para implementar y aplicar estilo a formularios sin encabezado.

**AEM Forms clásico (temáticas, editor de reglas, editor visual):** CSS personalizado, el editor de temáticas y el editor de reglas se aplican a la experiencia de creación de Forms adaptable clásica (sin encabezado). Para ver esos temas, consulte la [documentación de AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-forms.html) en Experience League.

## ¿Puede un formulario adaptable sin encabezado conectarse a cualquier CRM para leer o escribir datos?

Puede utilizar Microsoft Dynamics y Salesforce para enviar o rellenar previamente un formulario adaptable sin encabezado. Además de los CRM, los formularios adaptables sin encabezado admiten el envío o el relleno previo mediante puntos finales REST, correo electrónico y acciones de envío personalizadas.
