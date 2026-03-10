---
title: Prácticas recomendadas de Mobile Forms
description: En los casos de uso de formularios móviles y sin conexión, cree su propia aplicación nativa y recupere las definiciones de los formularios a través de la API de Forms adaptable sin encabezado. Método recomendado para aplicaciones móviles nativas.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: formularios móviles, aplicación nativa, formularios sin conexión, API sin encabezado
hide: false
exl-id: b8e2f1a4-5c6d-4e2a-9f3b-1d4e5a6c7b8d
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 7%

---

# Prácticas recomendadas de Mobile Forms {#mobile-forms-best-practices}

En los casos de uso de formularios móviles y sin conexión, el método recomendado es crear su propia aplicación nativa y recuperar las definiciones de formulario mediante la API de Forms adaptable sin encabezado. Esto le proporciona un control total sobre la experiencia móvil y garantiza una compatibilidad continua a medida que evolucionan las plataformas móviles.

## Enfoque recomendado {#recommended-approach}

Cree una aplicación móvil nativa (iOS o Android) que:

1. **Obtiene la definición del formulario sin encabezado**. Use las [API de Forms adaptables sin encabezado](https://opensource.adobe.com/aem-forms-af-runtime/api/) para recuperar el formulario JSON bajo demanda (por ejemplo, cuando el usuario abra un formulario o navegue a él en su aplicación). Puede enumerar los formularios disponibles y, a continuación, recuperar la definición del formulario por ID.

2. **Procesa el formulario en su aplicación**. Use su interfaz de usuario preferida (por ejemplo, React Native o vistas nativas) para procesar el formulario desde el JSON. Puede utilizar Forms Web SDK y los componentes de React de formularios adaptables sin encabezado existentes donde se ajusten a su pila o crear su propio procesador que consuma la misma estructura JSON.

3. **Opcionalmente admite sin conexión** - Implemente el almacenamiento local y sincronice en su aplicación. Por ejemplo, almacene en caché las definiciones de los formularios cuando estén en línea, guarde los borradores localmente y envíe o sincronice los datos cuando el dispositivo vuelva a estar en línea.

Este método mantiene la aplicación mantenible a medida que cambia Android y iOS, y utiliza la plataforma Forms adaptable sin encabezado compatible para la creación, validación y envío de formularios.

## Introducción {#getting-started}

* [Información general sobre formularios adaptables sin encabezado de AEM](overview.md): funcionalidades y conceptos.
* [API de formularios adaptables sin encabezado](https://opensource.adobe.com/aem-forms-af-runtime/api/): enumere, recupere, valide y envíe formularios mediante programación.
* [Arquitectura](architecture.md): cómo funcionan los formularios adaptables sin encabezado y cómo las aplicaciones front-end los consumen.

Para obtener una integración paso a paso, consulte [Crear y publicar un formulario sin encabezado](create-and-publish-a-headless-form.md) y el [Portal para desarrolladores](https://experienceleague.adobe.com/landing/aem-headless-forms/developer.html?lang=es).
