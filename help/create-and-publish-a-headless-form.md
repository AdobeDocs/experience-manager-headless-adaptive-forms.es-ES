---
title: Creación y publicación de un formulario sin encabezado con Adobe Experience Manager Adaptive Forms | Guía paso a paso
description: Aprenda a crear y publicar un formulario sin encabezado con los formularios adaptables de Adobe Experience Manager en esta guía paso a paso. Descubra las ventajas de quedarse sin encabezado y agilice el proceso de creación de formularios hoy mismo. Comience a crear formularios dinámicos y adaptables que funcionen sin problemas en todos los dispositivos con Formularios adaptables sin encabezado de Adobe Experience Manager.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 46%

---



# Creación y previsualización de un formulario sin encabezado mediante una aplicación React {#introduction}

<!-- Missing image ALT image tags -->

El kit de inicio le ayuda a empezar rápidamente mediante una aplicación React. Puede desarrollar y utilizar formularios adaptables sin encabezado en un Angular, Vanilla JS y otros entornos de desarrollo de su elección.

Comenzar con formularios adaptables sin encabezado es bastante fácil y rápido. Clone el proyecto React ya creado, instale las dependencias y ejecute el proyecto. Tiene un formulario adaptable sin encabezado integrado en una aplicación de React en ejecución. Puede utilizar el proyecto react de ejemplo para crear y probar formularios adaptables sin encabezado antes de implementarlos en un entorno de producción.

Vamos a empezar:

>[!NOTE]
>
>
> Esta guía de introducción utiliza una aplicación React. Puede utilizar la tecnología o el lenguaje de programación que prefiera para utilizar formularios adaptables sin encabezado.

## Antes de comenzar {#pre-requisites}

Para crear y ejecutar una aplicación React, debe tener instalado lo siguiente en su equipo:

* Instale la [última versión de Git](https://git-scm.com/downloads). Si es nuevo en Git, consulte [Instalación de Git](https://git-scm.com/book/es/v2/Getting-Started-Installing-Git).

* Instalar [Node.js 16.13.0 o posterior](https://nodejs.org/es/download/). <!-- URL is 404!! If you are new to Node.js, see [How to install Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs). -->

## Introducción

Una vez que cumpla los requisitos, realice los siguientes pasos para empezar:

1. [Configuración del kit de inicio de formularios adaptables sin encabezado](#setup)

1. [Vista previa del formulario adaptable sin encabezado incluido en el Starter Kit](#preview)

1. [Crear y procesar su propio formulario adaptable sin encabezado](#custom)



## &#x200B;1. Configurar el kit de inicio de formularios adaptables sin encabezado {#install}

El Starter Kit es una aplicación de React con un formulario adaptable sin encabezado de ejemplo y las bibliotecas correspondientes. Utilice el kit para desarrollar y probar sus formularios adaptables sin encabezado y los componentes de React correspondientes. Ejecute los siguientes comandos para configurar el Starter Kit de formularios adaptables sin encabezado:

1. Abra el símbolo del sistema y ejecute el siguiente comando:

   ```shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   El comando crea un directorio llamado **react-starter-kit-aem-headless-forms** en su ubicación actual y clona la aplicación de inicio React de formularios adaptables sin encabezado en él. Junto con las configuraciones y la lista de dependencias necesarias para procesar el formulario, el directorio incluye el siguiente contenido importante:

   * **Formulario de ejemplo**: el kit de inicio incluye un formulario de solicitud de préstamo de ejemplo. Para ver el formulario (definición de formulario) incluido con la aplicación, abra el archivo `/react-starter-kit-aem-headless-forms/form-definations/form-model.json`.
   * **Componentes de React de muestra**: el Starter Kit incluye componentes React de muestra para texto enriquecido y Slider. Esta guía le ayuda a crear sus propios componentes personalizados con estos componentes Texto enriquecido y Regulador.
   * **Mappings.ts**: el archivo mappings.ts le ayuda a asignar componentes personalizados con campos de formulario. Por ejemplo, asigne un campo de salto numérico con un componente de clasificación.
   * **Configuraciones del entorno**: las configuraciones de entorno le permiten elegir y procesar un formulario incluido en el kit de inicio o recuperar un formulario de un servidor de AEM Forms.

   ![](/help/assets/getting-started-starter-kit-content.png)

   >[!NOTE]
   >
   > 
   > Los ejemplos de los documentos se basan en VSCode. Puede utilizar cualquier editor de código de texto sin formato.


1. Vaya al directorio **react-starter-kit-aem-headless-forms** y ejecute el siguiente comando para instalar las dependencias:

   ```shell
   npm install
   ```

   El comando descarga todos los paquetes y bibliotecas necesarios para crear y ejecutar la aplicación, incluidas las bibliotecas de formularios adaptables sin encabezado (@aemforms/af-react-renderer, @aemforms/af-react-components, @adobe/react-spectrum). A continuación, ejecuta validaciones y conserva los datos de cada instancia de formulario.


   ![](/help/assets/install-react-app-starter-kit.png)


## &#x200B;2. Previsualizar el formulario adaptable sin encabezado {#preview}

Después de configurar el Starter Kit, puede obtener una vista previa del formulario adaptable sin encabezado de ejemplo y reemplazarlo por su propio formulario personalizado. También puede configurar el kit de inicio para recuperar un formulario de un servidor de AEM Forms. Para obtener una vista previa del formulario

1. Cambie el nombre del archivo `env_template` a `.env`. Asegúrese también de que la opción USE_LOCAL_JSON esté establecida en true.

   ![](/help/assets/rename-env-file.png)

   <!-- The options in the .env file help you configure source of the forms definantion (.JSON):
    *  To source forms definantion (.JSON) from an AEM Server, set USE_LOCAL_JSON option to false, use the AEM_URL option to specify URL  of your AEM Server, and set the AEM_FORM_PATH option to path of your adaptive form.
    *  To source forms definantion (.JSON) form-model.json file included in the starter-kit, set USE_LOCAL_JSON option to false. -->

1. Utilice el siguiente comando para ejecutar la aplicación:

   ```shell
     npm start
   ```


   Este comando inicia un servidor de desarrollo local y abre el formulario adaptable sin encabezado de ejemplo, incluido en la aplicación de inicio, en el explorador web predeterminado.

   ![Formulario sin encabezado de muestra](assets/sample-headless-adaptive-form.png)

   ¡Todo listo! Está listo para empezar a desarrollar un formulario adaptable personalizado sin encabezado.

   <!--  As you know, in a headless form the form data and logic are separate from the presentation layer and can be used by any client that can make HTTP requests, such as a mobile app, a static site, or a different web application. The form is often managed and stored on a server, which serves as the backend for the form. The client sends requests to the server to retrieve the form, submit data, and receive updated form data. This allows for greater flexibility and integration with different technologies. You can store and retrive a Headless Adaptive form on an AEM Server  -->

## &#x200B;3. Crear y procesar su propio formulario adaptable sin encabezado{#custom}

Un formulario adaptable sin encabezado representa el formulario y sus componentes, como campos y botones, en formato JSON (Notación de objetos de JavaScript). La ventaja de utilizar el formato JSON es que puede analizarse y utilizarse fácilmente en varios lenguajes de programación, lo que lo convierte en una forma cómoda de intercambiar datos de formulario entre sistemas. Para ver el formulario adaptable sin encabezado de ejemplo incluido en la aplicación, abra el archivo `/react-starter-kit-aem-headless-forms/form-definations/form-model.json`.

Vamos a crear un formulario `Contact Us` con cuatro campos: &quot;Nombre&quot;, &quot;Correo electrónico&quot;, &quot;Número de contacto&quot; y &quot;Mensaje&quot;. Los campos se definen como objetos (elementos) dentro del JSON, y cada objeto (elemento) tiene propiedades como tipo, etiqueta, nombre y obligatorio. El formulario también tiene un botón de tipo &quot;enviar&quot;. Este es el JSON del formulario.


```JSON
{
  "afModelDefinition": {
    "adaptiveform": "0.10.0",
    "items": [
      {
        "fieldType": "text-input",
        "label": {
          "value": "Name"
        },
        "name": "name"
      },
      {
        "fieldType": "text-input",
        "format": "email",
        "label": {
          "value": "Email"
        },
        "name": "email"
      },
      {
        "fieldType": "text-input",
        "format": "phone",
        "pattern": "[0-9]{10}",
        "label": {
          "value": "Contact Number"
        },
        "name": "Phone"
      },
      {
        "fieldType": "multiline-input",
        "label": {
          "value":"Message"
        },
        "name": "message"
      },
      {
        "fieldType": "button",
        "label":{
          "value": "Submit"
        },
        "name":"submit",
        "events":{
          "click": "submitForm()"
        }
      }
    ],
    "action": "https://eozrmb1rwsmofct.m.pipedream.net",
    "description": "Contact Us",
    "title": "Contact Us",
    "metadata": {
      "grammar": "json-formula-1.0.0",
      "version": "1.0.0"
    }
  }
}
```

>[!NOTE]
>
> * El atributo “afModelDefinition” solo es necesario para las aplicaciones de React y no forma parte de la definición del formulario.
> * Puede crear a mano el formulario JSON o utilizar el [editor de formularios adaptables de AEM (editor WYSIWYG de formularios adaptables)](create-a-headless-adaptive-form.md) para crear y enviar el formulario JSON. En un entorno de producción, se utiliza AEM Forms para enviar el formulario JSON, que se ampliará más adelante.
> * El tutorial utiliza https://pipedream.com/ para probar los envíos de formularios. Utiliza puntos de conexión propios o de terceros aprobados por su organización para recibir los datos de un formulario adaptable sin encabezado.


Para procesar el formulario, reemplace el formulario adaptable sin encabezado JSON de ejemplo `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` por el JSON anterior, guarde el archivo, espere a que el starter-kit se compile y actualice el formulario.

![Reemplace el formulario adaptable de ejemplo sin encabezado JSON `/react-starter-kit-aem-headless-forms/form-definations/form-model.json` por el formulario adaptable personalizado sin encabezado JSON](assets/render-custom-headless-adaptive-form.png)

<!-- Your form is ready. Let's add some validations and make "Name", "Email", and "Message" fields mandatory. -->

Ha procesado correctamente el formulario adaptable sin encabezado.


## Bonificación

Definamos el título de la página web que aloja el formulario en `Contact Us | WKND Adventures and Travel`. Para cambiar el título, abra el archivo _react-starter-kit-aem-headless-forms/public/index.html_ para editar y definir el título.

![](assets/contact-us-headless-adaptive-forms-updated-title.png)


## Siguiente paso

De forma predeterminada, el kit de inicio utiliza los componentes de la [gama de Adobe](https://spectrum.adobe.com/) para procesar el formulario. Puede crear y utilizar sus propios componentes o componentes de terceros. Por ejemplo, utilizando la IU de Google Material o la IU de Chakra.

Vamos a [usar la interfaz de usuario de Google Material](use-google-material-ui-react-components-to-render-a-headless-form.md) para procesar el formulario `Contact Us`.




