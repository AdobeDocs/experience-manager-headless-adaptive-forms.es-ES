---
title: Resolución de problemas de los formularios adaptables sin encabezado
description: Resolución de problemas de los formularios adaptables sin encabezado
keywords: sin encabezado, formulario adaptable, resolución de problemas
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
index: true
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
TQID: https://experienceleague.adobe.com/yjO3VhNmqIAyfnD7daHB7eAEUNmaAjnUgEm0fHc1ArY
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 12f711845becc93305717fb0c95e82355a8e97a5
workflow-type: tm+mt
source-wordcount: 152
ht-degree: 100%

---

# Solución de problemas

## No se puede implementar el proyecto basado en el arquetipo en el entorno de desarrollo local

### Problema

Cuando se usa `mvn -PautoInstallPackage clean install` o comandos similares para implementar un proyecto de arquetipo de AEM, el proyecto no consigue implementarse.

### Motivo

Puede deberse a una versión no compatible o a una instalación dañada de `node.js` o `NPM`.

### Solución

1. [Quite completamente las instalaciones actuales de Node.JS](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) de su entorno.

1. Instale `node.JS 16.13.0` o posterior con `NPM`.

1. Reinicie su equipo.


## El comando `mvn clean install` no consigue ejecutarse

### Problema

Cuando se usa `mvn clean install` o comandos similares para implementar un proyecto de arquetipo de AEM, el comando no consigue ejecutarse.

### Motivo

Puede suceder si Git no está instalado.

### Solución

Descargue e instale la [última versión de Git](https://git-scm.com/downloads). Si no tiene experiencia previa con Git, consulte [Instalación de Git](https://git-scm.com/book/es/v2/Getting-Started-Installing-Git).
