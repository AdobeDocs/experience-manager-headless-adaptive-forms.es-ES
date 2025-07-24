---
title: Habilitación de formularios adaptables sin encabezado en AEM Forms as a Cloud Service
description: Una guía paso a paso para habilitar formularios adaptables sin encabezado en AEM Forms as a Cloud Service, lo que simplifica la configuración y la activación en su entorno.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin
level: Beginner, Intermediate
contentOwner: Khushwant Singh
docset: CloudService
hide: true
hidefromtoc: true
exl-id: 7afff771-1296-4162-84c5-c8266b94af2f
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 74%

---

# Habilitación de formularios adaptables sin encabezado en AEM Forms as a Cloud Service {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

Al habilitar formularios adaptables sin encabezado en AEM Forms as a Cloud Service, puede empezar a crear, publicar y suministrar formularios sin encabezado mediante las instancias de Cloud Service de AEM Forms en varios canales. Se necesita un entorno habilitado para los componentes principales de formularios adaptables para utilizar formularios adaptables sin encabezado.

## Consideraciones

* Cuando se crea un nuevo programa as a Cloud Service de AEM Forms, [los formularios adaptables sin encabezado ya están habilitados para su entorno](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Si está ejecutando un programa as a Cloud Service de Forms anterior en el que los componentes principales están [no habilitados](#enable-components), primero [agregue las dependencias de los componentes principales de Forms adaptable](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) a su repositorio de Cloud Service. Implemente el repositorio actualizado en cada entorno para habilitar los formularios adaptables sin encabezado.

* Si su entorno de Cloud Service ya le permite [crear formularios adaptables basados en componentes principales](create-a-headless-adaptive-form.md), los formularios adaptables sin encabezado se habilitan automáticamente. A continuación, puede enviar estos formularios como experiencias sin encabezado a dispositivos móviles, web, aplicaciones nativas o cualquier servicio que los requiera.

>[!NOTE]
>
>
> Adobe proporciona un Starter Kit [de Forms adaptable (aplicación React)](create-and-publish-a-headless-form.md) para ayudar a los desarrolladores a empezar rápidamente con el desarrollo de Forms adaptable sin encabezado, sin habilitar Forms adaptable sin encabezado en el entorno de AEM Forms as a Cloud Service. Puede habilitar los formularios adaptables sin encabezado en un entorno Forms as a Cloud Service más tarde después de un [rápido tutorial práctico con el desarrollo de formularios sin encabezado](create-and-publish-a-headless-form.md).

## Habilitación de formularios adaptables sin encabezado para un entorno AEM Forms as a Cloud Service

Realice los siguientes pasos, en el orden indicado, para habilitar los formularios adaptables sin encabezado para un entorno AEM Forms as a Cloud Service

<!-- Missing image ALT tag -->
![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## &#x200B;1. Clone su repositorio de Git de AEM Forms as a Cloud Service {#clone-git-repository}

1. Inicie sesión en [Cloud Manager](https://my.cloudmanager.adobe.com/) y seleccione su organización y programa.

1. Vaya a la tarjeta de **Canalizaciones** desde la página **Información general del programa**.

1. Haga clic en el botón **Acceder a la info del repositorio** para acceder y administrar su repositorio Git. La página incluye la siguiente información:

   * La dirección URL del repositorio de Git de Cloud Manager.
   * Credenciales del nombre de usuario del repositorio de Git (nombre de usuario y contraseña).

   Pulse en **Generar contraseña** para ver o generar la contraseña.

1. Abra el terminal o el símbolo de comando en el equipo local de su ordenador y ejecute el siguiente comando:

   ```Shell
   git clone [Git Repository URL]
   ```

   Cuando se le solicite, proporcione las credenciales. El repositorio se clona en su ordenador local.


## &#x200B;2. Añadir dependencias de componentes principales de formularios adaptables al repositorio de Git {#add-adaptive-forms-core-components-dependencies}

1. Abra la carpeta del repositorio de Git en un editor de código de texto sin formato. Por ejemplo, VS Code.
1. Abra el archivo `[AEM Repository Folder]\pom.xml` para editarlo.
1. Reemplazar versiones de `core.forms.components.version`, `core.forms.components.af.version` y `core.wcm.components.version` componentes con versiones especificadas en [documentación de componentes principales](https://github.com/adobe/aem-core-forms-components). Si el componente no existe, añada estos componentes.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![Mencione la versión más reciente de los componentes principales de formularios](/help/assets/latest-forms-component-version.png)

1. En la sección de dependencias del archivo `[AEM Repository Folder]\pom.xml`, agregue las siguientes dependencias y guarde el archivo.

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. Abra el archivo `[AEM Repository Folder]/all/pom.xml` para editarlo. Agregue las siguientes dependencias en la sección `<embeddeds>` y guarde el archivo.

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  Reemplace `${appId}` con su appId.
   >
   >  Para encontrar su `${appId}`, en el archivo `[AEM Repository Folder]/all/pom.xml`, busque el término `-packages/application/install`. El texto antes del término `-packages/application/install` es su `${appId}`. Por ejemplo, el siguiente código, `myheadlessform` es `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. En la `<dependencies>` sección del archivo `[AEM Repository Folder]/all/pom.xml`, agregue las siguientes dependencias y guarde el archivo:

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. Abra `[AEM Repository Folder]/ui.apps/pom.xml` para editarlo. Añada la dependencia `af-core bundle` y guarde el archivo.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >Asegúrese de que los siguientes artefactos de componentes principales de formularios adaptables no estén incluidos en el proyecto.
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > y
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. Guarde y cierre el archivo.

## &#x200B;3. Actualice el proyecto para incluir la versión más reciente de los componentes principales de Forms:

1. Abra la [carpeta de proyecto de arquetipo de EAM]/pom.xml para su edición.


1. Guarde y cierre el archivo.

## &#x200B;4. Confirme las actualizaciones en el repositorio de Git y ejecute una canalización para desplegar el repositorio {#Commit-the-updates-to-your-git-repository}

1. Para confirmar el código en el repositorio de Git:
   1. Abra el terminal o el símbolo del comando.
   1. Navegue hasta su `[AEM Repository Folder]` y ejecute los siguientes comandos en el orden indicado

      ```Shell
      git add pom.xml
      git add all/pom.xml
      git add ui.apps/pom.xml
      git commit -m "Added dependencies for Adaptive Forms Core Components"
      git push origin
      ```

1. Una vez que los archivos se hayan confirmado en el repositorio de Git, [Ejecute la canalización](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/using/code-deployment).

   Una vez que la ejecución de la canalización se haya realizado correctamente, los componentes principales de Forms adaptable se habilitan para el entorno correspondiente. Además, se añade una plantilla de formularios adaptables (componentes principales) y una temática de Canvas 3.0 al entorno as a Cloud Service de formularios, lo que le proporciona opciones para personalizar y crear componentes principales basados en formularios adaptables.


## Preguntas frecuentes {#faq}

### ¿Cuáles son los componentes principales? {#core-components}

Los [componentes principales](https://experienceleague.adobe.com/es/docs/experience-manager-core-components/using/introduction) son un conjunto de componentes estandarizados de administración de contenido web (WCM) para AEM a fin de acelerar el tiempo de desarrollo y reducir el costo de mantenimiento de los sitios web.

### ¿Qué capacidades completas se añaden al habilitar los componentes principales? {#core-components-capabilities}

Cuando los componentes principales de formularios adaptables se habilitan para su entorno, se agrega a este una plantilla de formulario adaptable basada en componentes principales en blanco y una temática de Lienzo 3.0. Tras habilitar los componentes principales de formularios adaptables para su entorno, puede:

* Crear componentes principales basados en formularios adaptables.
* Crear componentes principales basados en plantillas de formulario adaptable.
* Crear temáticas personalizadas para componentes principales basadas en plantillas de formulario adaptable.
* Proporcione representaciones JSON de un formulario adaptable basado en componentes principales a canales como móvil, web, apps nativas y servicios que requieren la representación sin encabezado de un formulario.

### ¿Los componentes principales de formularios adaptables están habilitados para mi entorno? {#enable-components}

Para comprobar que los componentes principales de Formularios adaptables están habilitados para su entorno:

1. [Clone su repositorio as a Cloud Service de AEM Forms](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Abra el archivo `[AEM Repository Folder]/all/pom.xml` del repositorio de Git del Cloud Service de AEM Forms.

1. Busque las siguientes dependencias:

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![busque el artefacto de core-forms-components-af-core en all/pom.xml](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Si existen dependencias, los componentes principales de Formularios adaptables se habilitan para su entorno.
