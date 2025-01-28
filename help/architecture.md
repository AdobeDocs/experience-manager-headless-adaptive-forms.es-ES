---
title: Arquitectura de los formularios adaptables sin encabezado
description: Obtenga información acerca de la arquitectura de Formularios adaptables sin encabezado de AEM Forms y cómo puede ayudarle a crear rápidamente formularios para varias plataformas. En este artículo se ofrece información sobre cómo trabajan los formularios adaptables sin encabezado y cómo se pueden integrar con diferentes aplicaciones para simplificar el proceso de creación de formularios.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: sin encabezado, formulario adaptable, arquitectura
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: c46ac28e490a09d6f563c4b5673d30a53c277a69
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 97%

---


# ¿Cómo funciona el formulario adaptable sin encabezado?

Un formulario adaptable sin encabezado es esencialmente una estructura (esquema) JSON que consta de campos de formulario (cuadro de texto, opciones y muchos más campos) y reglas correspondientes (lógica condicional) para añadir un comportamiento interactivo al formulario. Puede utilizar las API de REST en su aplicación o sitio web para solicitar la estructura JSON alojada y procesar de forma nativa la estructura JSON como un formulario de su aplicación o sitio web. Un único formulario adaptable sin encabezado puede servir para varias páginas web y aplicaciones sin realizar ningún cambio en la aplicación o en el sitio web.

![Funcionamiento del formulario adaptable sin encabezado](/help/assets/how-headless-adaprive-forms-work.png)

## Arquitectura {#architecture}

Una arquitectura de formularios adaptables típica sin encabezado constituye un servidor de Adobe Experience Manager Forms, formularios adaptables sin encabezado alojados en el servidor de Adobe Experience Manager Forms y sus aplicaciones de front-end (sitio web, aplicación móvil, aplicaciones JavaScript, aplicaciones de chat y mucho más) para representaciones de formularios específicas del canal.

La arquitectura típica de una implementación de formularios adaptables sin encabezado tiene el siguiente aspecto:

![Arquitectura](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### Componente de una implementación de formularios adaptables sin encabezado

**Servidor de Adobe Experience Manager**: además de servir de host para los formularios adaptables sin encabezado, Adobe Experience Manager proporciona las siguientes capacidades back-end:

* Las API de RESTful permiten enumerar, recuperar, rellenar previamente, validar, enviar y rastrear el estado de envío de formularios sin encabezado.
* Editor visual para desarrollar fácilmente un formulario adaptable sin encabezado.
* Modelo de datos de Forms para recibir o enviar datos a fuentes de datos diferentes.
* Motor de flujos de trabajo para automatizar tareas complejas.

**Formularios adaptables sin encabezado**: un formulario adaptable sin encabezado se representa como un archivo .json. La estructura JSON define los componentes, las restricciones y la estructura de un formulario.

**Aplicaciones front-end**: las aplicaciones de front-end como SPA (aplicaciones de una sola página), aplicaciones móviles, aplicaciones JavaScript, consumen formularios adaptables sin encabezado (la representación de formulario JSON) y procesan el formulario en un cliente. Puede utilizar el componente de procesamiento React suministrado con los formularios adaptables sin encabezado para procesar un formulario adaptable o crear su propio componente personalizado para procesar de forma nativa formularios adaptables sin encabezado.

<!-- ### Understanding Headless adaptive forms definition -->



### Herramientas para desarrolladores

En un ciclo de desarrollo típico, comience creando y alojando formularios adaptables sin encabezado en el servidor de Adobe Experience Manager Forms. En el segundo paso, debe asignar los componentes de la IU o utilizar una biblioteca de componentes de IU pública, como la IU de Material Google o la IU de Chakra, para aplicar el estilo a sus formularios. En el último paso, recuperará y visualizarán formularios adaptables sin encabezado de su aplicación (sitio web, aplicación móvil, aplicaciones JavaScript, aplicaciones de chat o muchas otras superficies).

Las siguientes herramientas le ayudan a crear e integrar formularios adaptables sin encabezado en sus aplicaciones:

**SDK web de Forms (tiempo de ejecución del lado del cliente)**: el SDK web de Forms es una biblioteca JavaScript del lado del cliente. Permite aplicar validaciones del lado del cliente en los campos del formulario, mantener el estado del formulario y proporcionar enlaces para conectar el formulario con la capa de IU o el componente procesado de los formularios adaptables. Permite que los clientes validen las restricciones aplicadas a varios campos de un formulario y enlaces para conectar la estructura JSON del formulario al marco de trabajo de la IU. El SDK web de Forms tiene los siguientes componentes:

* **Procesador de reglas empresariales**: el procesador de reglas empresariales acepta la estructura JSON de los formularios como entrada, administra el estado de los campos del formulario, ejecuta las reglas y ejecuta los controladores de sucesos presentes en el JSON.
* **Enlazador de React**: proporciona enlaces sobre el controlador para añadir estado a los componentes del formulario. También resulta útil para rellenar previamente un formulario.
* **Biblioteca de componentes**: proporciona componentes del espectro de React y utiliza enlaces en el módulo Enlazador de React para añadir estado a esos componentes.

Además de proporcionar las API para validar las restricciones aplicadas a varios campos de un formulario, el SDK web de Forms proporciona enlaces para conectar formularios adaptables sin encabezado al marco de trabajo de la IU. También facilita el procesador React para formularios adaptables sin encabezado para ayudarle a integrarlos en su aplicación. Los siguientes componentes del SDK web están disponibles:

* **[@aemforms/af-react-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-react-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

Todos estos componentes se incluyen en el Arquetipo de AEM. Cuando se crea un proyecto basado en el arquetipo AEM 37 o posterior para formularios adaptables sin encabezado, se incluye en el proyecto la versión más reciente de las bibliotecas incluidas anteriormente.

* **Área de reproducción de código**: [Área de reproducción de código](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=en) es un entorno interactivo diseñado para que los desarrolladores experimenten, aprendan y prueben las capacidades de Forms adaptable sin encabezado.

**Aplicación iniciada**: Adobe también ha lanzado una aplicación para ayudarle a comenzar rápidamente con los formularios adaptables sin encabezado.

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**Storybook**: [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) proporciona información general sobre los diferentes componentes de los formularios adaptables sin encabezado. También proporciona una lista de todos los componentes admitidos, sus correspondientes propiedades y restricciones.

**Extensión de código de Visual Studio**: [extensión de código de Visual Studio](visual-studio-code-extension-for-headless-adaptive-forms.md) para crear una estructura JSON válida. Proporciona soporte y validación de IntelliSense para la estructura JSON de formularios junto con funciones comunes como añadir, eliminar o cambiar el nombre de componentes de una estructura JSON.

**API de HTTP y Java Script**: las [API de HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) le permiten enumerar, recuperar, validar, enviar y seguir el estado de envío de los formularios sin encabezado. Las [API de JS](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) le ayuda a utilizar formularios adaptables sin encabezado con cualquier marco de IU basado en JavaScript.

**Fórmula JSON**: es una implementación de la gramática de la expresión de formularios para que le ayude a consultar la estructura JSON y a crear reglas para formularios adaptables sin encabezado. La gramática es una combinación de funciones y operadores similares a hojas de cálculo y [JMESPath](https://jmespath.org/) es un lenguaje de consulta JSON. Puede usar el [sitio de pruebas](https://opensource.adobe.com/json-formula/dist/index.html) para explorar la sintaxis y las capacidades de la fórmula JSON.

**Especificaciones de Formularios adaptables sin encabezado versión 2.0** la especificación de Formularios adaptables versión 2.0 proporciona información detallada sobre todos los componentes, restricciones y métodos disponibles para definir formularios adaptables sin encabezado. La especificación está disponible en formato [PDF](/help/assets/headless-adaptive-forms-specification.pdf).

