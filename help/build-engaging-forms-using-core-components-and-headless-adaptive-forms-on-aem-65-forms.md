---
title: Creación de formularios atractivos con componentes principales y sin encabezado
description: Cree una Forms atractiva con los componentes principales y sin encabezado.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
topic-tags: develop
hide: true
exl-id: 07a71aac-de38-4839-b8d6-b47c3f575eb3
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 67%

---

# Genere formularios atractivos utilizando componentes principales y formularios adaptables sin encabezado en AEM 6.5 Forms {#build-engaging-forms-using-core-components-and-headless}

<!-- This article and many others in this entire repo are completely missing the image ALT tags (descriptions) for each added image asset. That is impacting the CQI score for Experience Manager in a negative way. Be sure you take the time to add the required missing image ALT tags.  -->

## Información general del laboratorio {#lab-overview}

En este laboratorio práctico, aprenderá a utilizar AEM Forms con los componentes principales más recientes (alineados con AEM Sites) para crear formularios adaptables rápidamente. Ofrezca estos formularios como experiencias sin encabezado a canales web, móviles y de chat para una captura de datos omnicanal sin problemas. También aprenderá las prácticas recomendadas sobre el estilo, las personalizaciones y el desarrollo front-end.

## Puntos clave {#key-takeaways}

* **Agilidad del negocio**: como usuario empresarial, puedo crear fácilmente experiencias de formularios para varios canales.

* **Capacidad de desarrollador front-end**: como desarrollador front-end, puedo controlar la experiencia del usuario final mediante formularios sin encabezado.

* **Velocidad de desarrollo**: como desarrollador, puedo personalizar fácilmente y de forma coherente los componentes de Sites y Forms.

## Antes de comenzar {#pre-requisites}

Para utilizar este laboratorio práctico:

* Instale la [última versión de Git](https://git-scm.com/downloads). Si es nuevo en Git, consulte [Instalación de Git](https://git-scm.com/book/es/v2/Getting-Started-Installing-Git).

* Instalar [Node.js 16.13.0 o posterior](https://nodejs.org/es/download/). <!-- URL IS 404! If you are new to Node.js, see [How to install Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).-->

* [Habilitar Forms adaptable sin encabezado](enable-headless-adaptive-forms-and-core-components.md) en su entorno de AEM 6.5 Forms.

* Instale [Microsoft Visual Studio Code](https://code.visualstudio.com/download) o cualquier editor de texto sin formato. Los ejemplos de este documento utilizan código de Microsoft Visual Studio.

## Lección 1 {#lesson-1}

### Objetivo {#lesson-1-objectives}

Familiarícese con el entorno de AEM 6.5 Forms.

### Contexto de la lección {#lesson-1-context}

En esta lección, se familiarizará con AEM 6.5 navegando por la interfaz de usuario.

### Ejercicio {#lesson-1-excercise}

1. Abra el explorador e introduzca la dirección URL del entorno de creación de Por ejemplo:
   [https://localhost:4502](https://localhost:4502).

1. Una vez que haya iniciado sesión, vaya a la IU de AEM Forms. Haga clic en **Formularios**.

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. Haga clic en **Formularios y documentos**. Descarte cualquier elemento emergente relacionado con las preferencias o la información.

   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   Se muestran todos los formularios disponibles.

   ![](/help/assets/screenshot2028114029.png){width="50%" align="left"}

## Lección 2

### Objetivo

Cree un formulario adaptable utilizando los componentes principales más recientes, configúrelo y envíelo.

### Contexto de la lección

Como usuario empresarial, utilizará el editor de Forms adaptable y sus componentes principales listos para usar para crear un formulario adaptable. A continuación, puede enviar el formulario a los canales web, móvil y de chat para capturar datos.

### Ejercicio

1. Cree un punto final de envío para el formulario:

   1. Abra <https://pipedream.com/requestbin> en una nueva pestaña del explorador.
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. Haga clic en **Crear un grupo público** y copie la dirección URL del punto final.
      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

   Este punto final en particular sirve como ejemplo para enviar y ver datos. En la producción real, se utiliza un punto final propio o fuentes de datos para almacenar los datos capturados.

1. Cree un formulario adaptable:

   1. En la pestaña del explorador que se usa en la lección 1, vaya a la interfaz web de AEM Forms y luego a **Forms** > **Forms y documentos**.

   1. Haga clic en **Crear** y seleccione Formulario adaptable.
      ![](/help/assets/creating-adaptive-form-6-5.png){width="50%" align="left"}

   1. Seleccione la plantilla **En blanco con componentes principales** en la pantalla de selección de plantillas como se muestra a continuación y pulse **Siguiente**.
      ![](/help/assets/creating-adaptive-form-6-5-select-blank-template.png){width="50%" align="left"}

   1. Especifique `Contact us` como **Título** del formulario. Asegúrese de que la variable **Nombre** del formulario es `contact-us`.
      ![](/help/assets/creating-adaptive-form-65-specify-title.png){width="50%" align="left"}

   1. Haga clic en **Crear**. Se muestra un cuadro de diálogo.

   1. En el cuadro de diálogo, haga clic en **Editar**. El formulario se abrirá en el editor de formularios adaptables. Descarte cualquier ventana emergente o diálogo para obtener preferencias o información.

   1. Abra el explorador de componentes y arrastre y suelte el componente Panel en medio de la pantalla.

      ![](/help/assets/lab65-add-panel.png){width="50%" align="left"}

   1. Arrastre y suelte los componentes desde el Explorador de componentes para crear un formulario, de forma similar a lo siguiente:

      ![](/help/assets/contact-us-headless-adaptive-form.png){width="50%" align="left"}


   1. Abra el Explorador de contenido, haga clic en el icono Propiedades del contenedor de la guía y abra la ficha **Envío**.

   1. Seleccione la acción de envío **Enviar al extremo REST**

   1. Seleccione la opción **Habilitar la solicitud POST** y especifique el extremo REST creado en la lección 2 en el cuadro de texto **URL para la solicitud POST**; a continuación, haga clic en el icono **Listo**.

      ![](/help/assets/configure-submit-action.png){width="50%" align="left"}

1. Publique un formulario adaptable:

   1. Abra la interfaz de usuario de AEM, vaya hasta **Formularios** > **Formularios y documentos**. Seleccione el formulario creado en el paso anterior y haga clic en **`Publish`**.

   1. En el cuadro de diálogo **Publicar Assets**, haga clic en **Publicar**. Se muestra el mensaje de éxito.

## Lección 3

### Objetivo

Actualice los estilos utilizando las prácticas recomendadas de desarrollo front-end.

### Contexto de la lección

En esta lección, como desarrollador front-end, aprenderá a actualizar fácilmente el estilo del formulario adaptable creado anteriormente.

### Ejercicio

Configure un repositorio local de la temática:

1. Abra el símbolo del sistema o shell con derechos de administrador:

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. En el símbolo del sistema, utilice el siguiente comando para ir hasta la carpeta `c:\git`.

   ```Shell
   cd git
   ```

   Si la carpeta no existe, utilice el comando `md git` para crearla.

1. Use el siguiente comando para clonar el código front-end del tema:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```

1. Use el siguiente comando en el orden de la lista para ir al directorio **aem-forms-theme-canvas** y abra Visual Studio Code.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png){width="50%" align="left"}

1. Seleccione **Confiar en los autores de todos los archivos de la carpeta principal** y haga clic en **Sí, confío en los autores**.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. Cambie el nombre del archivo `env_template` archivo a .env.  Para cambiar el nombre, haga clic con el botón derecho en el archivo **env_template** y seleccione la opción **Cambiar nombre**.

   ![](/help/assets/screenshot2028116429.png){width="30%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. Establezca los siguientes valores para las variables del archivo .env y guarde el archivo:

   * **AEM_URL**: especifica la URL de una instancia de **publicación**. Por ejemplo, `https://localhost:4502/`

   * **AEM_ADAPTIVE_FORM**: especifique el nombre del formulario. Por ejemplo, `contact-us`.

   </br>

   ![](/help/assets/lab65-theme-environment-variable.png)


1. En la ventana Símbolo del sistema, ejecute el siguiente comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Si recibe un mensaje pidiéndole que actualice `npm` mediante el comando `npm notice Run npm nstall -g npm@9.6.0`, ignore el mensaje.
   > * A menos que se le indique en el libro, no ejecute otros comandos de `npm`.

1. Ahora, ejecute el siguiente comando para obtener una vista previa del formulario.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   Una vez ejecutado el comando anterior, espere al mensaje `webpack compiled`. El formulario se muestra en la pestaña del explorador.

   >[!NOTE]
   >
   >Si aparece una pantalla en blanco en el explorador después de ejecutar el comando `npm run live` durante más de 3 a 4 minutos, cambie `localhost` en la dirección URL del explorador a 127.0.0.1 y pulse **Intro**.


   ![](/help/assets/contact-us-headless-adaptive-form-with-canvas-theme.png){width="50%" align="left"}


1. En Visual Studio Code, abra el archivo `PROJECT\src\site\_variables.scss`. Observe que el color de `$error` es un tono de rojo.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. En el explorador, envíe el formulario para ver el color rojo en el campo **Nombre**.

   ![](/help/assets/error-color-before.png)

1. Configure el color del **$error** en **#5736eb**, y guarde el archivo.

1. Actualice el explorador y envíe el formulario. Observe que el color del error en el campo de nombre ha cambiado en consecuencia.

   ![](/help/assets/error-color-after.png)

1. En el símbolo del sistema, presione **CTRL+C**, escriba **Y** y presione la tecla **Intro** para finalizar el proceso npm. Es importante detener el servidor npm para que no entre en conflicto con el siguiente conjunto de ejercicios.
1. Cierre las ventanas de Visual Studio Code y del símbolo del sistema.

## Lección 4

### Objetivo

Procese el formulario en interfaces web/móviles y de otro tipo como un formulario sin encabezado.

### Contexto de la lección

En esta lección, como desarrollador de front-end, aprenderá a procesar el formulario adaptable creado anteriormente como un formulario sin encabezado mediante un marco de trabajo de diseño de React spectrum.

### Ejercicio

Configure un repositorio local con el proyecto de inicio React:

1. Abra el símbolo del sistema con derechos de administrador.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. En el símbolo del sistema, utilice el siguiente comando para ir hasta la carpeta `c:\git`.

   ```Shell
   cd git
   ```

1. Utilice el siguiente comando para clonar el proyecto de inicio de reacción del formulario adaptable:

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028117329.png)

1. Utilice los siguientes comandos en el orden de la lista para ir al directorio **react-starter-kit-aem-headless-forms** y abra Visual Studio Code.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028117529.png)


   Se abre la ventana de Visual Studio Code.

   ![](/help/assets/screenshot2028117429.png){width="50%" align="left"}

Para procesar el formulario alojado en su entorno de publicación:

1. Cambie el nombre del archivo env_template al archivo .env. Para cambiar el nombre, haga clic con el botón derecho en el archivo **env_template** y seleccione la opción **Cambiar nombre**.

   ![](/help/assets/screenshot2028117629.png){width="30%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. Establezca los siguientes valores para las variables del archivo .env. Después de actualizar las variables, guarde el archivo.

   * **AEM_URL**: especifique la URL del entorno de publicación. Por ejemplo, `https://localhost:4503/`

   * **AEM_FORM_PATH**: especifique la ruta del formulario adaptable creado en la lección anterior. Por ejemplo, `/content/forms/af/contact-us/`

   </br>

   ![](/help/assets/lab65-starter-kit-environment-variable.png)

1. Abra la ventana de comandos, asegúrese de que está en el directorio **react-starter-kit-aem-headless-forms** y ejecute el siguiente comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. En la ventana Símbolo del sistema, ejecute el siguiente comando:

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-starter-kit-start.png)

   El comando anterior inicia el servidor de desarrollo local que procesa la definición del formulario recuperada de AEM de una forma sin encabezado utilizando la biblioteca de front-end del espectro de reacción.

   >[!NOTE]
   >
   > 
   > Si aparece una pantalla en blanco en el explorador después de ejecutar el comando `npm start` durante más de 3 a 4 minutos, cambie `localhost` en la dirección URL del explorador a 127.0.0.1 y pulse **Intro**.

   ![](/help/assets/headless-adaptive-form-lab.png)

Haga cambios en el formulario del servidor como usuario empresarial y vea los cambios reflejados automáticamente en el formulario sin encabezado.

1. Abra la interfaz de administración de AEM Forms en el explorador. Por ejemplo, [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).

1. Seleccione el formulario **Contáctenos** y haga clic en **Editar.** Abre el formulario en el editor de formularios adaptables.


1. Seleccione el campo **Número de contacto** y haga clic en el **icono Editar (icono de lápiz)** en la barra de herramientas. Si no puede ver la barra de herramientas emergente, cambie al modo Editar. Haga clic en el botón **Editar** en la parte superior derecha e izquierda del botón **Vista previa**.

   ![](/help/assets/change-field-title.png){width="50%" align="left"}

1. Cambie la etiqueta a **Número de móvil**. Haga clic en cualquier espacio vacío del formulario y se guardarán los cambios realizados en él.

Vamos a publicar el formulario actualizado para propagar los cambios en el entorno publicado.

1. En la pestaña de la interfaz de administración de AEM Forms, seleccione el formulario de contacto y haga clic en **Cancelar la publicación**. Si no ve el botón **Cancelar la publicación**, vaya al paso 3 para publicar los cambios directamente.


1. Haga clic en **Cancelar la publicación**. Haga clic en **Cerrar** en el cuadro de diálogo correspondiente.

1. Después de actualizar el explorador, seleccione el formulario de contacto y haga clic en **Publicar**.


1. Haga clic en **Publicar**. Haga clic en **Cerrar** en el cuadro de diálogo correspondiente.

1. Actualice la pestaña del explorador con el formulario sin encabezado mostrado. Tenga en cuenta que la etiqueta Número de contacto ha cambiado a Número de móvil.

   ![](/help/assets/headless-adaptive-form.png)

1. Abra la ventana del símbolo del sistema que se utiliza para iniciar el proyecto **react-starter-kit-aem-headless-forms**, pulse **CTRL+C** y, a continuación, introduzca **Y** y pulse la tecla Intro para terminar el proceso de npm. Es importante detener el servidor npm para que no entre en conflicto con el siguiente conjunto de ejercicios.

1. Cierre las ventanas de Visual Studio Code y del símbolo del sistema.


## Lección 5

### Objetivo

Procesar el formulario como un formulario sin encabezado utilizando la IU de Google Material

### Contexto de la lección

En esta lección, como desarrollador de front-end, aprenderá a procesar el formulario adaptable creado anteriormente como un formulario sin encabezado mediante la IU de Google Material.

### Ejercicio

Configure un repositorio local con el proyecto de inicio de la interfaz de usuario de Material:

1. Abra el símbolo del sistema con derechos de administrador.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. En el símbolo del sistema, utilice el siguiente comando para ir hasta la carpeta `c:\git`.

   ```Shell
   cd git
   ```

1. Ejecute los siguientes comandos en el orden indicado para crear una carpeta denominada `mui` y desplazarse a la carpeta `mui` mediante los siguientes comandos:

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Utilice el siguiente comando para clonar el proyecto de inicio de reacción del formulario adaptable:

   ```Shell
   git clone -b mui-lab https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028126529.png)

1. Utilice el siguiente comando en el orden de la lista para ir a la carpeta **react-starter-kit-aem-headless-forms** y abra el código en Visual Studio Code:

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028126829.png)

Para procesar el formulario alojado en su entorno de publicación:

1. Cambie el nombre del archivo **env_template** al archivo **.env**. Para cambiar el nombre, haga clic con el botón derecho en el archivo **env_template** y seleccione **Cambiar nombre**.

   ![](/help/assets/screenshot2028126629.png){width="30%" align="left"}

1. Establezca los siguientes valores para las variables del archivo .env. Después de actualizar las variables, guarde el archivo. Utilice la combinación de teclas **CTRL + S** para guardar el archivo.

   * **AEM_URL**: especifique la URL del entorno de publicación. Por ejemplo, [https://localhost:4503](https://localhost:4503)

   * **AEM_FORM_PATH**: especifique la ruta del formulario adaptable creado en la lección anterior. Por ejemplo, /content/forms/af/contact-us/


1. Abra la ventana de comandos, asegúrese de que está en el directorio **react-starter-kit-aem-headless-forms** y ejecute el siguiente comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. En la ventana Símbolo del sistema, ejecute el siguiente comando:

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-mui-starter-kit-start.png)

   El comando inicia un servidor de desarrollo local y procesa la definición de formulario recuperada de AEM en una forma sin encabezado mediante la biblioteca de front-end de la IU de Google Material.

   >[!NOTE]
   >
   >Si aparece una pantalla en blanco en el explorador después de ejecutar el comando `npm start` durante más de 3 a 4 minutos, cambie `localhost` en la dirección URL del explorador a 127.0.0.1 y pulse **Intro**.

   ![](/help/assets/google-mui-form.png)

## Lección 6

### Objetivo

Crear una apariencia alternativa del formulario sin encabezado mediante las variaciones de los componentes de la IU de Material

### Contexto de la lección

Como desarrollador front-end, aprenderá a crear versiones alternativas de la interfaz de usuario de Material de varios componentes en esta lección. También las aplicará al formulario adaptable que el usuario empresarial creó anteriormente.

### Ejercicio

Actualice la variación de los componentes en el proyecto sin encabezado. Cambiar la variante del componente de entrada de texto de la IU de material a `OutlinedInput`:

1. En Visual Code, vaya al componente de entrada de texto abriendo el archivo `index.tsx` en `src/components/textinput/index.tsx`.

1. Agregue `//` al principio de la línea de código 104. Convierte la línea en un comentario.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Agregue lo siguiente en la línea 105 para utilizar una variante diferente del componente y guardar el archivo. Utilice la combinación de teclas **CTRL + S** para guardar el archivo.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/aem65-lab-code-update.png)

   Es esencial utilizar mayúsculas correctas para la variante &#39;OutinedInput&#39;; de lo contrario, la compilación fallaría. La compilación del entorno de desarrollo local comienza automáticamente con el símbolo del sistema. Espere hasta que vea el siguiente mensaje

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Actualice el explorador, si no se actualiza automáticamente, para ver cómo el componente de entrada de texto utiliza una variante diferente.

   ![](/help/assets/screenshot2028127729.png){width="50%" align="left"}


   Este cambio se produce para usuarios finales sin ningún cambio en la definición del formulario en el servidor de AEM Forms y es específico para el canal sin encabezado que se está considerando. Por ejemplo, un canal web en este laboratorio.

   ![](/help/assets/aem65-lab-mui-style-update.png)


1. Cierre las ventanas de Visual Studio Code y del símbolo del sistema.

## Preguntas más frecuentes

+++ ¿Los componentes principales están disponibles públicamente?

Sí, los componentes principales de formularios adaptables están disponibles con AEM 6.5 Forms as Cloud Service. Necesita el Service Pack 16 o posterior de AEM Forms 6.5 para utilizar los componentes principales de formularios adaptables.

+++

+++ ¿Los formularios sin encabezado requieren una licencia independiente?

No, los formularios sin encabezado utilizan la misma métrica de valor de licencia y el mismo número de envíos de formularios.

+++




## Pasos siguientes

Ahora sabe cómo crear formularios adaptables y entregarlos en varios canales con formularios sin encabezado. Utilice esas habilidades para crear experiencias de captura de datos escalables y de alta calidad independientemente de dónde se encuentren los usuarios.

## Recursos

* [Introducción a los componentes principales del formulario adaptable](https://experienceleague.adobe.com/es/docs/experience-manager-core-components/using/adaptive-forms/introduction)

* [Creación de formularios adaptables con componentes principales](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components)

* [Actualización del estilo para el AF basado en componentes principales](https://experienceleague.adobe.com/es/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components)

* [Formularios adaptables sin encabezado](https://experienceleague.adobe.com/en/docs/experience-manager-headless-adaptive-forms/using/overview)

* [Uso de un kit de inicio React sin encabezado](https://experienceleague.adobe.com/en/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form)
