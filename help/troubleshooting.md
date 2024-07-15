---
title: Resolución de problemas de los formularios adaptables sin encabezado
description: Resolución de problemas de los formularios adaptables sin encabezado
keywords: sin encabezado, formulario adaptable, resolución de problemas
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 100%

---

# Solución de problemas

## No se puede implementar el proyecto basado en el arquetipo en el entorno de desarrollo local

### Problema

Cuando se usa `mvn -PautoInstallPackage clean install` o comandos similares para implementar un proyecto de arquetipo AEM, el proyecto no consigue implementarse.

### Motivo

Puede deberse a una versión no compatible o a una instalación dañada de node.js o NPM.

### Solución

1. [Quite completamente las instalaciones actuales de Node.JS](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) de su entorno.

1. Instale Node.JS 16.13.0 o posterior con NPM.

1. Reinicie su equipo.


## El comando `mvn clean install` no consigue ejecutarse

### Problema

Cuando se usa `mvn clean install` o comandos similares para implementar un proyecto de arquetipo AEM, el comando no se puede ejecutar.

### Motivo

Puede suceder si Git no está instalado.

### Solución

Descargue e instale la [última versión de Git](https://git-scm.com/downloads). Si no tiene experiencia previa con Git, consulte [Instalación de Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
