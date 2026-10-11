---
title: Problemas conocidos con los formularios adaptables sin encabezado
description: Problemas conocidos con los formularios adaptables sin encabezado.
keywords: sin encabezado, formulario adaptable, problemas conocidos
hide: true
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
source-git-commit: b34afbc4f692b81838ad6947895c9b347dff6d62
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 100%
---

# Problemas conocidos {#known-issues}

* No se admiten patrones de edición, visualización y datos. (CQ-4327047)
* La restricción minItems no se puede cambiar dinámicamente. (CQ-4342499)
* Las validaciones a nivel de panel, si se violan, no arrojan ningún error. (CQ-4342373)
* Las validaciones de archivos, si se violan, no arrojan ningún error. (CQ-4342372)
* Las propiedades personalizadas no son dinámicas. (CQ-4342376)
* Cambiar los datos del archivo dinámicamente en un evento de cambio usando expresiones conduce a un bucle infinito. (CQ-4342377)
* El archivo adjunto no admite texto de ayuda. (CQ-4342370)
* La casilla de verificación obligatoria no muestra un error durante el envío, si no está seleccionada. (CQ-4342371)
* aria-label no se añade en el archivo adjunto. (CQ-4341494)
