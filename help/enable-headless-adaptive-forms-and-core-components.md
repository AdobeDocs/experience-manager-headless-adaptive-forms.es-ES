---
title: Habilitación de formularios adaptables sin encabezado en AEM 6.5 Forms
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM 6.5 Forms
description: Aprenda a habilitar formularios adaptables sin encabezado en AEM 6.5 Forms con nuestra guía paso a paso. Nuestro tutorial le guiará por el proceso, lo que facilita la integración de esta potente función en su sitio web y la mejora de su experiencia de usuario.
seo-description: Learn how to enable headless adaptive forms on AEM 6.5 Forms with our step-by-step guide. Our tutorial walks you through the process, making it easy to integrate this powerful feature into your website and improve your user experience.
contentOwner: Khushwant Singh
role: Admin
exl-id: e1a5e7e0-d445-4cca-b8d7-693d9531f075
source-git-commit: 999c3d092d03d7a82363bc94ce79ceb33bf0df7e
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 100%

---

# Habilitación de formularios adaptables sin encabezado en AEM 6.5 Forms {#enable-headless-adaptive-forms-on-aem-65-forms}

Para habilitar Formularios adaptables sin encabezado en el entorno de AEM 6.5 Forms configure un proyecto basado en el arquetipo 41 o posterior de AEM e impleméntelo en todas las instancias de autor y publicación.

Al implementar el proyecto basado en el arquetipo 41 o posterior en las instancias de AEM 6.5 Forms, puede tener la posibilidad de [crear formularios adaptables basados en componentes principales](create-a-headless-adaptive-form.md). Estos formularios se representan en formato JSON y se utilizan como formularios adaptables con encabezado y sin encabezado, lo que permite una mayor flexibilidad y personalización en una amplia gama de canales, incluidas aplicaciones móviles, web y nativas.

## Requisitos previos {#prerequisites}

Antes de habilitar formularios adaptables sin encabezado en el entorno de AEM 6.5 Forms,

* [Actualizar al Service Pack 16 de AEM 6.5 Forms (6.5.16.0) o posterior](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=es).

* Instalar la última versión de [Apache Maven](https://maven.apache.org/download.cgi).

* Instale un editor de texto sin formato. Por ejemplo, Microsoft Visual Studio Code.

## Crear e implementar el último proyecto basado en el arquetipo de AEM

Para crear un proyecto basado en el arquetipo de AEM 41 o [posterior](https://github.com/adobe/aem-project-archetype) e implementarlo en todas las instancias de autor y publicación:

1. Inicie sesión en el equipo, aloje y ejecute la instancia de AEM 6.5 Forms como administrador.
1. Abra el símbolo de comando o el terminal.
1. Ejecute el siguiente comando para crear un proyecto basado en el arquetipo 41 de AEM:

   * Microsoft Windows

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
      -D archetypeGroupId=com.adobe.aem ^
      -D archetypeArtifactId=aem-project-archetype ^
      -D archetypeVersion=41 ^
      -D appTitle="My Form" ^
      -D appId="myform" ^
      -D groupId="com.myform" ^
      -D includeFormsenrollment="y" ^
      -D aemVersion="6.5.15" 
   ```

   * Linux o Apple macOS

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
      -D archetypeGroupId=com.adobe.aem \
      -D archetypeArtifactId=aem-project-archetype \
      -D archetypeVersion=41 \
      -D appTitle="My Form" \
      -D appId="myform" \
      -D groupId="com.myform" \
      -D includeFormsenrollment="y" \
      -D aemVersion="6.5.15" 
   ```

   Cuando ejecute el comando anterior, asegúrese de tener en cuenta los siguientes puntos:

   * Actualice el comando para reflejar los valores específicos de su entorno, incluidos appTitle, appId y groupId. Además, establezca los valores de includeFormsenrollment en &#39;y&#39;. Si utiliza el Portal de Forms, establezca la opción _includeExamples=y_ para que incluya los componentes principales del Portal de Forms en el proyecto.

   * No cambie “aemVersion” de 6.5.15.0 por nada más.

1. (Solo para proyectos basados en la versión 41 del arquetipo) Una vez creado el proyecto de arquetipo de AEM, habilite las temáticas para formularios adaptables basados en componentes principales. Para habilitar las temáticas, haga lo siguiente:

   1. Abra la [Carpeta de proyecto de arquetipo de AEM]/ui.apps/src/main/content/jcr_root/apps/__appId__/components/adaptiveForm/page/customheaderlibs.html para editarla:

   1. Agregue el siguiente código en la línea 21:

      ```XML
      <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
      data-sly-use.formstructparser="com.adobe.cq.forms.core.components.models.form.FormStructureParser"
      data-sly-test.themeClientLibRef="${formstructparser.themeClientLibRefFromFormContainer}">
      <sly data-sly-test="${themeClientLibRef}" data-sly-call="${clientlib.css @ categories=themeClientLibRef}"/>
      </sly>
      ```

      ![Agregue el código mencionado anteriormente en la línea 21](/help/assets/code-to-enable-themes.png)

   1. Guarde y cierre el archivo.

1. Actualizar el proyecto para que incluya la última versión de los componentes principales de Forms:

   1. Abra la [Carpeta de proyecto de arquetipo de AEM]/pom.xml para editarla.
   1. Establezca la versión de `core.forms.components.version` y `core.forms.components.af.version` a la versión [Últimos componentes principales de Forms](https://github.com/adobe/aem-core-forms-components/tree/release/650).

      ![Mencione la versión más reciente de los componentes principales de formularios](/help/assets/latest-forms-component-version.png)

   1. Guarde y cierre el archivo.


1. Una vez que el proyecto de arquetipo de AEM se haya creado correctamente, cree el paquete de implementación para su entorno. Haga clic para generar el paquete:

   1. Vaya al directorio raíz del proyecto del arquetipo de AEM.


   1. Ejecute el siguiente comando para compilar el proyecto de arquetipo de AEM para su entorno:

      ```Shell
      mvn clean install
      ```

      ![archetypebuild-success](assets/corecomponent-build-successful.png)


   Una vez que el proyecto de arquetipo de AEM se haya compilado correctamente, se generará un paquete de AEM. Puede encontrar el paquete en [Carpeta de proyecto de arquetipo de AEM]\all\target\[appid].all-[versión].zip

1. Utilice el [Administrador de paquetes](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=es) para implementar la [Carpeta de proyecto de arquetipo de AEM]\all\target\[appid].all-[versión].zip en el entorno de instancias de autor y publicación.

>[!NOTE]
>
>
>
>Si tiene dificultades para acceder al cuadro de diálogo de inicio de sesión en una instancia de publicación para instalar el paquete a través del Administrador de paquetes, intente iniciar sesión a través de la siguiente URL: http://[URL del servidor de publicación]:[PUERTO]/system/console. Esto le permite acceder al inicio de sesión en la instancia de publicación, lo que le permite continuar con el proceso de instalación.


Los componentes principales están habilitados para su entorno. Se implementan una plantilla de formularios adaptables basados en componentes principales en blanco y una temática de Lienzo 3.0 que le permiten [crear formularios adaptables basados en los componentes principales](create-a-headless-adaptive-form.md).

## Preguntas frecuentes

### ¿Qué son los componentes principales?

Los [componentes principales](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=es) son un conjunto de componentes estandarizados de la administración de contenido web (WCM) para AEM con el objetivo de acelerar el tiempo de desarrollo y reducir el coste de mantenimiento de sus sitios web.

### ¿Qué funcionalidades completas se añaden al habilitar los componentes principales?


Cuando los componentes principales de formularios adaptables se habilitan para su entorno, se agrega a este una plantilla de formulario adaptable basada en componentes principales en blanco y una temática de Lienzo 3.0. Tras habilitar los componentes principales de formularios adaptables para su entorno, puede:

* Crear componentes principales basados en formularios adaptables.
* Crear componentes principales basados en plantillas de formulario adaptable.
* Crear temáticas personalizadas para componentes principales basadas en plantillas de formulario adaptable.
* Proporcione representaciones JSON de un formulario adaptable basado en componentes principales a canales como mobile, web, apps nativas y servicios que requieren la representación sin encabezado de un formulario.
