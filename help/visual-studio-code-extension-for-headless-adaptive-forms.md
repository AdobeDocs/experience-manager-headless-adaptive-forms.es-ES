---
title: Extensión de Visual Studio Code para formularios adaptables sin encabezado
description: Extensión de Visual Studio Code para formularios adaptables sin encabezado
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: formularios adaptables, sin encabezado, extensión de Visual Studio Code
hide: false
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
source-git-commit: 47ac7d03c8c4fa18ac3bdcef04352fdd1cad1b16
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 100%

---

# Extensión de Microsoft Visual Studio Code para formularios adaptables sin encabezado

Si utiliza código de Microsoft® Visual Studio como IDE, puede utilizar la extensión de formularios adaptables para Microsoft Visual Studio Code. La extensión es la siguiente:

* Agrega funciones de IntelliSense para formularios adaptables a Visual Studio Code
* Ayuda a validar y completar automáticamente la sintaxis JSON para componentes de formularios adaptables sin encabezado
* Proporciona un panel para navegar fácilmente por la estructura de un formulario adaptable sin encabezado
* Ayuda a traducir un formulario adaptable sin encabezado

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## Requisitos previos

* Descargar e instalar [Microsoft Visual Studio Code 1.62.0 o posterior](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version). Si tiene una versión anterior o no tiene ninguna instalada, descargue la más reciente del [Sitio web de Microsoft](https://code.visualstudio.com/docs/setup/setup-overview). Para utilizar Visual Studio desde la línea de comandos en Apple macOS, consulte [Iniciar desde la línea de comandos](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).
* Descargue la [extensión del creador de formularios adaptables](/help/assets/adaptive-form-builder-0.12.0.vsix).

## Instalar la extensión

1. Abra el símbolo del sistema y vaya al directorio que contiene el archivo de extensión descargado, *adaptive-form-builder-[version].vsix*.

1. Ejecute el siguiente comando para iniciar la extensión:

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![Instalación de la extensión](/help/assets/install-extension.png)


   Para obtener información sobre los archivos .vsix, consulte [Ayuda de Visual Studio Code](https://code.visualstudio.com/docs/editor/extension-marketplace#_install-from-a-vsix).
