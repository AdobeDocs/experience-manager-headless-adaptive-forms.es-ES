---
title: Creación de formularios atractivos con componentes principales y sin encabezado
seo-title: Build Engaging Forms Using Core Components and Headless
description: Creación de formularios atractivos con componentes principales y sin encabezado
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
exl-id: d0ca7389-9a7a-421e-ab6b-7845813d860e
source-git-commit: f489a2ba818db44ccd92df80a177f0e9f3a1bc2c
workflow-type: ht
source-wordcount: '2479'
ht-degree: 100%

---

# Creación de formularios atractivos con componentes principales y sin encabezado Habilitación de formularios adaptables sin encabezado en AEM Forms as a Cloud Service {#build-engaging-forms-using-core-components-and-headless}

## Información general del laboratorio {#lab-overview}

En este laboratorio práctico, aprenderá lo siguiente:

Cómo utilizar AEM Forms para crear fácilmente formularios adaptables utilizando los componentes principales más recientes que son coherentes con AEM Sites, habilitar experiencias de captura de datos omnicanal al enviar los formularios adaptables como formularios sin encabezado a la web, dispositivos móviles y chat. También aprenderá las prácticas recomendadas sobre el estilo, las personalizaciones y el desarrollo front-end.

## Puntos clave {#key-takeaways}

* **Agilidad del negocio**: como usuario empresarial, puedo crear fácilmente experiencias de formularios para varios canales.

* **Capacidad de desarrollador front-end**: como desarrollador front-end, puedo controlar la experiencia del usuario final mediante formularios sin encabezado.

* **Velocidad de desarrollo**: como desarrollador, puedo personalizar fácilmente y de forma coherente los componentes de Sites y Forms.

## Requisitos previos {#prerequisites}

Para usar este laboratorio práctico:

* Instale la [última versión de Git](https://git-scm.com/downloads). Si es nuevo en Git, consulte [Instalación de Git](https://git-scm.com/book/es/v2/Getting-Started-Installing-Git).

* Instale [Node.js 16.13.0 o posterior](https://nodejs.org/es/download/). Si no tiene experiencia previa con Node.js, consulte [Cómo instalar Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).

* [Habilite formularios adaptables sin encabezado](enable-headless-adaptive-forms-and-core-components-on-forms-cloud-service.md) para su entorno AEM Forms as a Cloud Service.

* Instale [Microsoft Visual Studio Code](https://code.visualstudio.com/download) o cualquier editor de texto sin formato. Los ejemplos del documento utilizan código de Microsoft Visual Studio Code.



## Lección 1 {#lesson-1}

### Objetivo {#lesson-1-objectives}

Familiarícese con el entorno de AEM Forms as a Cloud Service.

### Contexto de la lección {#lesson-1-context}

En esta lección, puede familiarizarse con el entorno de AEM Forms as a Cloud Service navegando por la interfaz de usuario.

### Ejercicio {#lesson-1-excercise}

1. Abra el explorador e introduzca la dirección URL del entorno de creación de Cloud Service. Por ejemplo:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Inicie sesión en el entorno de creación de Cloud Service.

1. Para ir hasta la interfaz de usuario de AEM Forms, haga clic en **Formularios > Formularios y documentos**.

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   Descarte cualquier elemento emergente relacionado con las preferencias o la información. Se muestran todos los formularios disponibles.


## Lección 2

### Objetivo

Cree un formulario adaptable utilizando los componentes principales más recientes, configúrelo y envíelo.

### Contexto de la lección

En esta lección, como usuario empresarial, creará un formulario adaptable para varios canales como web, móvil y chat mediante la creación de formularios adaptables con componentes principales listos para usarse estandarizados para la captura de datos.

### Ejercicio

1. Cree un punto final de envío para el formulario:

   1. Abra <https://requestbin.com/> en una nueva pestaña del explorador.
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. Haga clic en **Crear un grupo público** y copie la dirección URL del punto final.
      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

1. Cree un formulario adaptable mediante la interfaz del asistente:

   1. En la pestaña del explorador utilizada en la Lección 1, vaya a la interfaz web de AEM Forms as Cloud Service y a Formularios y documentos.
      ![](/help/assets/screenshot2028114029.png)

   1. Haga clic en **Crear** y seleccione Formulario adaptable.
      ![](/help/assets/screenshot2028114629.png)

   1. Seleccione la plantilla **En blanco con componentes principales** de la pantalla de selección de plantillas como se muestra a continuación:
      ![](/help/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Haga clic en la pestaña **Estilo** y seleccione **wknd-theme** como se muestra a continuación:
      ![](/help/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Haga clic en la pestaña **Envío** y seleccione la tarjeta **Enviar al punto final de REST** y especifique el grupo público en
      el campo **URL de la petición POST** como se muestra a continuación:
      ![](/help/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Haga clic en **Crear**. Especifique un nombre y título para el formulario. Por ejemplo, **registro**. Haga clic en **Crear**.

   1. Se abre el editor de formularios adaptables. Descarte cualquier ventana emergente o diálogo para obtener preferencias o información. Haga clic en el explorador de componentes en el carril izquierdo y añada los componentes **Encabezado** y **Pie de página**, respectivamente, en la parte superior e inferior del formulario en blanco.
      ![](/help/assets/screenshot2028121929.png)

   1. Arrastre y suelte los componentes desde el Explorador de componentes para crear un formulario, de forma similar a lo siguiente:

      ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}





1. Agregue validaciones al formulario:

   1. Haga clic en el componente **Número de teléfono** para que se muestre el menú emergente. Haga clic en el componente **icono de llave inglesa** en el menú para configurar el campo.

   1. Abra la **pestaña Validaciones**, marque el campo **Requerido** y haga clic en **Listo**. Se muestra el mensaje de éxito.
      ![](/help/assets/screenshot2028123529.png){width="50%" align="left"}

      ![](/help/assets/screenshot2028123629.png){width="50%" align="left"}

1. Previsualice y envíe el formulario.

   1. Haga clic en **Vista previa** para obtener una vista previa del formulario desde la perspectiva de usuario final.

   1. Rellene el formulario con datos ficticios.

   1. Enviar el formulario.
      ![](/help/assets/screenshot2028125729.png)

   1. En la pestaña Grupo de solicitudes, compruebe los datos enviados.
      ![](/help/assets/screenshot2028125829.png)

1. Agregue interactividad al formulario con reglas:

   1. Haga clic en el componente **Marque la casilla para recibir un 5 % de descuento**. En la barra de herramientas de opciones, haga clic en el icono Reglas. Se abre la opción Editor de reglas.

   1. Cree una regla: cuando la opción **Marque la casilla para recibir un 5 % de descuento** está seleccionada, las opciones para aplicar tarjeta de crédito están desactivadas.

1. Publicar el formulario.

   1. Abra la interfaz de administración de AEM Forms, por ejemplo, `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments` y seleccione el formulario.

   1. Haga clic en **Publicar**.

      ![](/help/assets/screenshot2028115629.png)

      Se muestra el mensaje de éxito.

      ![](/help/assets/screenshot2028115729.png)

      La URL de publicación del formulario es similar a `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

   1. Para ver el formulario publicado, reemplace el ID de programa (pXXXXXX) y el ID de entorno (eXXXXXX) en la URL anterior con los ID de su
entorno.

## Lección 3

### Objetivo

Actualice los estilos utilizando las prácticas recomendadas de desarrollo front-end.

### Contexto de la lección

En esta lección, como desarrollador front-end, aprenderá a actualizar fácilmente el estilo del formulario adaptable creado anteriormente.

### Ejercicio

Configure el repositorio local del tema:

1. Abra el símbolo del sistema o shell con derechos de administrador:

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. En el símbolo del sistema, utilice el siguiente comando para desplazarse a la carpeta **c:\git**

   ```Shell
   cd c:\git
   ```

1. Use el siguiente comando para clonar el código front-end del tema:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Use el siguiente comando en el orden de la lista para ir al directorio **aem-forms-theme-canvas** y abra Visual Studio Code.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png)

1. Seleccione **Confiar en los autores de todos los archivos de la carpeta principal** y haga clic en **Sí, confío en los autores**.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. Para procesar el formulario alojado en el entorno de publicación de su servicio en la nube, cambie el nombre del archivo `env_template`.  Para cambiar el nombre, haga clic con el botón derecho en el archivo **env_template** y seleccione la opción **Cambiar nombre**.

   ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. Establezca los siguientes valores para las variables del archivo .env y guarde el archivo:

   * **AEM_URL**: especifique el entorno de publicación de su servicio en la nube. Por ejemplo, `https://publish-p105303-e986623.adobeaemcloud.com/`. 

   * **AEM_ADAPTIVE_FORM**: especifique la ruta del formulario. Por ejemplo, si la ruta del formulario es `/content/forms/af/registration`, el valor de esta variable sería `registration`.

     ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}


1. En la ventana Símbolo del sistema, ejecute el siguiente comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Si recibe un mensaje pidiendo que actualice npm a través del comando `npm notice Run npm nstall -g npm@9.6.0`, ignore el mensaje.
   > * No ejecute otros comandos npm a menos que se indique en el libro de trabajo.

1. Ejecute el siguiente comando para obtener una vista previa del formulario.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   Una vez ejecutado el comando anterior, espere al mensaje `webpack compiled`. El formulario se muestra en la pestaña del explorador.

   >[!NOTE]
   >
   >Si aparece una pantalla en blanco en el explorador después de ejecutar el comando `npm run live` durante más de tres o cuatro minutos, cambie `localhost` en la dirección URL del explorador a 127.0.0.1 y pulse **Intro**.


   ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}


1. En Visual Studio Code, abra el archivo `PROJECT\src\site\_variables.scss`. Observe que el color de `$error` es un tono de rojo.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. En el explorador, envíe el formulario para ver el color rojo en el campo **Nombre**.

   ![](/help/assets/screenshot2028120829.png)

1. Configure el color del **$error** en **#5736eb**, y guarde el archivo.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Actualice el explorador y envíe el formulario. El color del error del aviso en el campo de nombre ha cambiado como corresponde.

   ![](/help/assets/screenshot2028121129.png)

1. En el símbolo del sistema, presione **CTRL+C**, escriba **Y**, y pulse la tecla **Intro** para finalizar el proceso de npm. Es importante detener el servidor npm para que no entre en conflicto con el siguiente conjunto de ejercicios.
1. Cierre las ventanas de Visual Studio Code y del símbolo del sistema.

## Lección 4

### Objetivo

Procese el formulario en web/móvil y otras interfaces como un formulario sin encabezado.

### Contexto de la lección

En esta lección, como desarrollador de front-end, aprenderá a procesar el formulario adaptable creado anteriormente como formulario sin encabezado mediante el marco de trabajo de diseño del espectro de reacción.

### Ejercicio

Configure el repositorio local mediante el proyecto de inicio de reacción:

1. Abra el símbolo del sistema con derechos de administrador.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. En el símbolo del sistema, utilice el siguiente comando para desplazarse a la carpeta **c:\git**

   ```Shell
   cd c:\git
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

Para procesar el formulario alojado en el entorno de publicación de su servicio en la nube, haga lo siguiente:

1. Cambie el nombre del archivo env_template a .env. Para cambiar el nombre, haga clic con el botón derecho en el archivo **env_template** y seleccione la opción **Cambiar nombre**.

   ![](/help/assets/screenshot2028117629.png){width="50%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. Establezca los siguientes valores para las variables del archivo .env. Después de actualizar las variables, guarde el archivo.

   * **AEM_URL**: especifique la URL del entorno de publicación del servicio en la nube. Por ejemplo, `https://publish-p105303-e986623.adobeaemcloud.com`. 

   * **AEM_FORM_PATH**: especifique la ruta del formulario adaptable creado en la lección anterior. Por ejemplo, `/content/forms/af/registration/`. 

     ![](/help/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Abra la ventana Comandos, compruebe que se encuentra en el directorio react-starter-kit-aem-headless-forms y ejecute el siguiente comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. En la ventana Símbolo del sistema, ejecute el siguiente comando:

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028118129.png)

   El comando anterior inicia el servidor de desarrollo local que procesa la definición del formulario recuperada de AEM de una forma sin encabezado utilizando la biblioteca de front-end del espectro de reacción.

   >[!NOTE]
   >
   > 
   > Si aparece una pantalla en blanco en el explorador después de ejecutar el comando `npm start` durante más de tres o cuatro minutos, cambie `localhost` en la dirección URL del explorador a 127.0.0.1 y pulse **Intro**.

   ![](/help/assets/screenshot2028118229.png)

Comprobemos la ejecución de las reglas de esta forma sin encabezado:

1. Seleccione la opción **Marque la casilla para recibir un 5 % de descuento**. La opción posterior para solicitar tarjeta de crédito está desactivada.

   ![](/help/assets/screenshot2028126229.png)

1. Desactive **Marque la casilla para recibir un 5 % de descuento** para habilitar la opción de tarjeta de crédito.

   ![](/help/assets/screenshot2028126329.png)

Haga cambios en el formulario del servidor como usuario empresarial y vea los cambios reflejados automáticamente en el formulario sin encabezado.

1. Abra la interfaz de administración de AEM Forms en el explorador. Por ejemplo, [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. Seleccione el formulario **Contáctenos** y haga clic en **Editar.** Abre el formulario en el editor de formularios adaptables.


1. Seleccione el campo **Número de teléfono** y haga clic en el **icono Editar (icono de lápiz)** en la barra de herramientas. Si no puede ver la barra de herramientas emergente, cambie al modo de edición haciendo clic en el botón **Editar** en la parte superior derecha, a la izquierda del botón **Vista previa**.

   ![](/help/assets/screenshot2028119629.png)

1. Cambie la etiqueta a Número de móvil. Haga clic en cualquier espacio vacío del formulario y se guardarán los cambios realizados en él.

   ![](/help/assets/screenshot2028119729.png)

Publique el formulario actualizado para propagar los cambios al entorno de publicación.

1. En la pestaña de la interfaz de administración de AEM Forms, seleccione el formulario de registro y haga clic en **Cancelar la publicación**. Si no ve el botón **Cancelar la publicación**, vaya al paso 3 para publicar los cambios directamente.

1. Haga clic en **Cancelar la publicación**. Haga clic en **Cerrar** en el cuadro de diálogo correspondiente.

1. Después de actualizar el explorador, seleccione el formulario de registro y haga clic en **Publicar**.

1. Haga clic en **Publicar**. Haga clic en **Cerrar** en el cuadro de diálogo correspondiente.

1. Actualice la pestaña del explorador con el formulario sin encabezado mostrado. Tenga en cuenta que la etiqueta de número de teléfono ha cambiado a Número de móvil.

   ![](/help/assets/screenshot2028120529.png)

1. Abra la ventana del símbolo del sistema que se utiliza para iniciar el proyecto **react-starter-kit-aem-headless-forms**, pulse **CTRL+C** y, a continuación, introduzca **Y** y pulse la tecla Intro para finalizar el proceso de npm. Es importante detener el servidor npm para que no entre en conflicto con el siguiente conjunto de ejercicios.

1. Cierre las ventanas de Visual Studio Code y del símbolo del sistema.


## Lección 5

### Objetivo

Procesar el formulario como un formulario sin encabezado utilizando la IU de Google Material

### Contexto de la lección

En esta lección, como desarrollador de front-end, aprenderá a procesar el formulario adaptable creado anteriormente como formulario sin encabezado mediante la IU de Google Material.

### Ejercicio

Configure el repositorio local mediante el proyecto de inicio de la IU de Material:

1. Abra el símbolo del sistema con derechos de administrador.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}


1. En el símbolo del sistema, utilice el siguiente comando para desplazarse a la carpeta **c:\git**:

   ```Shell
   cd c:\git
   ```

1. Ejecute los siguientes comandos en el orden indicado para crear una carpeta denominada mui y vaya a esta utilizando los siguientes comandos:

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

Para procesar el formulario alojado en el entorno de publicación de su servicio en la nube, haga lo siguiente:

1. Cambie el nombre del archivo **env_template** a **.env**. Para cambiar el nombre, haga clic con el botón derecho en el archivo **env_template** y seleccione **Cambiar nombre**.

   ![](/help/assets/screenshot2028126629.png){width="50%" align="left"}

1. Establezca los siguientes valores para las variables del archivo .env. Después de actualizar las variables, guarde el archivo. Utilice la combinación de teclas **CTRL + S** para guardar el archivo.

   * **AEM_URL**: especifique la URL del entorno de publicación del servicio en la nube. Por ejemplo, [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: especifique la ruta del formulario adaptable creado en la lección anterior. Por ejemplo, /content/forms/af/registration/

     ![](/help/assets/screenshot2028126929.png)

1. Abra la ventana de comandos, asegúrese de que está en el directorio **react-starter-kit-aem-headless-forms** y ejecute el siguiente comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. En la ventana Símbolo del sistema, ejecute el siguiente comando:

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028127129.png)

   El comando inicia un servidor de desarrollo local y procesa la definición de formulario recuperada de AEM en una forma sin encabezado mediante la biblioteca de front-end de la IU de Google Material.

   >[!NOTE]
   >
   >Si aparece una pantalla en blanco en el explorador después de ejecutar el comando `npm start` durante más de tres o cuatro minutos, cambie `localhost` en la dirección URL del explorador a 127.0.0.1 y pulse **Intro**.

   ![](/help/assets/screenshot2028127229.png)

1. Para evaluar la ejecución de la misma lógica empresarial en esta representación de formulario:

   Seleccione **Marque la casilla para recibir un 5 % de descuento**. La opción siguiente **¿Desea solicitar el formulario de tarjeta de crédito corporativa We.Finance?** se deshabilita.

   ![](/help/assets/screenshot2028127329.png){width="50%" align="left"}

## Lección 6

### Objetivo

Crear una apariencia alternativa del formulario sin encabezado mediante las variaciones de los componentes de la IU de Material

### Contexto de la lección

En esta lección, como desarrollador front-end, aprenderá a crear una representación alternativa de diferentes componentes mediante la IU de Material para el formulario adaptable creado anteriormente por el usuario empresarial.

### Ejercicio

Actualice la variación de los componentes en el proyecto sin encabezado. Cambiar la variante del componente de entrada de texto de la IU de material a `OutlinedInput`:

1. En Visual Code, vaya al componente de entrada de texto abriendo el archivo `index.tsx` en `src/components/textinput/index.tsx`.

1. Agregue `//` al principio de la línea de código 103. Convierte la línea en un comentario.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Agregue lo siguiente en la línea 104 para utilizar una variante diferente de componente y guardar el archivo. Utilice la combinación de teclas **CTRL + S** para guardar el archivo.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/screenshot2028127629.png)

   Es esencial utilizar correctamente las mayúsculas y minúsculas para la variante “OutinedInput”, de lo contrario la compilación fallaría. La compilación del entorno de desarrollo local comienza automáticamente con el símbolo del sistema. Espere hasta que vea el siguiente mensaje

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Actualice el navegador, si no se actualiza automáticamente, para ver que el componente de entrada de texto utiliza una variante diferente.

   ![](/help/assets/screenshot2028127729.png)


   Este cambio se produce para usuarios finales sin ningún cambio en la definición del formulario en el servidor de AEM Forms y es específico para el canal sin encabezado que se está considerando. Por ejemplo, el canal web en este laboratorio.

   ![](/help/assets/screenshot2028127529.png){width="50%" align="left"}


1. Cierre las ventanas de Visual Studio Code y del símbolo del sistema.

## Preguntas más frecuentes

+++ ¿Está disponible públicamente el asistente de Formularios adaptables?

Sí, está disponible con AEM Forms como Cloud Service.

+++


+++ ¿Los componentes principales están disponibles públicamente?

Sí, los componentes principales de Formularios adaptables están disponibles con AEM Forms como Cloud Service.

+++

+++ ¿Los formularios sin encabezado están disponibles públicamente?

Sí, los formularios sin encabezado están disponibles con AEM Forms como Cloud Service.

+++

+++ ¿Los formularios sin encabezado requieren una licencia independiente?

No, los formularios sin encabezado utilizan la misma métrica de valor de licencia y el mismo número de envíos de formularios.

+++

+++ ¿Los Componentes principales y los formularios sin encabezado están disponibles con AEM 6.5 Forms?

Sí, tanto los componentes principales de los formularios adaptables como los formularios sin encabezado están disponibles con el Service Pack 16 y posteriores de AEM Forms 6.5.

+++


## Pasos siguientes

Ahora que ha aprendido a crear formularios adaptables y distribuirlos en varios canales mediante formularios sin encabezado, puede intentar poner en práctica sus nuevas habilidades. Diviértase y siga creando y ofreciendo experiencias de captura de datos excepcionales a sus usuarios finales, donde estén, a mayor escala.

## Recursos

* [Introducción a los componentes principales del formulario adaptable](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=es)

* [Creación de formularios adaptables con componentes principales](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=es)

* [Actualización del estilo para el AF basado en componentes principales](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=es)

* [Formularios adaptables sin encabezado](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=es)

* [Uso del kit de inicio React sin encabezado](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=es)
