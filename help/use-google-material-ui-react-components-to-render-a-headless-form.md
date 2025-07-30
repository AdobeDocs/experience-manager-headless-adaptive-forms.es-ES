---
title: Utilice los componentes React de la IU de Google Material para procesar un formulario sin encabezado
description: Obtenga información sobre cómo utilizar los componentes React de la IU de Google Material para procesar un formulario sin encabezado. Esta guía exhaustiva le guía por el proceso paso a paso para crear componentes personalizados de formularios adaptables sin encabezado para asignar y utilizar los componentes React de la IU de Google Material para aplicar estilo a un formulario adaptable sin encabezado.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: 476509d5-f4c1-4d1c-b124-4c278f67b1ef
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: ht
source-wordcount: '870'
ht-degree: 100%

---


# Utilice una biblioteca de React personalizada para procesar un formulario sin encabezado

<!-- This article is completely missing the image ALT tags (descriptions) for each added image asset. That is impacting the CQI score for Experience Manager in a negative way. Be sure you add the required missing image ALT tags.  -->

Puede crear e implementar componentes personalizados para personalizar el aspecto y la funcionalidad (comportamiento) de los formularios adaptables sin encabezado según los requisitos y las directrices de su organización.

Estos componentes tienen dos propósitos principales: controlar el aspecto o el estilo de los campos de formulario y almacenar los datos recopilados a través de estos campos en la instancia del modelo de formulario. Si esto suena confuso, no se preocupe. En breve explorará estos propósitos con más detalle. Por ahora, vamos a centrarnos en los pasos iniciales de la creación de componentes personalizados, el procesamiento del formulario mediante estos componentes y la utilización de eventos para guardar y enviar datos a un punto final REST.

En este tutorial, los componentes de la IU de Google Material se emplean para mostrar cómo procesar un formulario adaptable sin encabezado utilizando componentes React personalizados. Sin embargo, no está limitado a esta biblioteca y puede utilizar cualquier biblioteca de componentes React o desarrollar sus propios componentes personalizados.

Al concluir este artículo, el formulario _Contact Us_ (contáctenos) creado en el artículo [Creación y publicación de un formulario sin encabezado con el kit de inicio](create-and-publish-a-headless-form.md) se transformará en lo siguiente:

![](assets/headless-adaptive-form-with-google-material-ui-components.png)


Los pasos principales que hay que seguir al utilizar los componentes de IU de Google Material para procesar un formulario son:

![](assets/headless-forms-graphics-source-main.svg)

## &#x200B;1. Instalar la IU de Google Material

De forma predeterminada, el kit de inicio utiliza los componentes [Espectro de Adobe](https://spectrum.adobe.com/). Vamos a definirlo para utilizar la [IU de materiales de Google](https://mui.com/):

1. Asegúrese de que el kit de inicio no está en funcionamiento. Para detener el kit de inicio, abra el terminal, vaya a **react-starter-kit-aem-headless-forms** y pulse Ctrl-C (es lo mismo en Windows, Mac y Linux®).

   No intente cerrar el terminal. El cierre del terminal no detiene el kit de arranque.

1. Ejecute el siguiente comando:

```shell
    
    npm install @mui/material @emotion/react @emotion/styled --force
    
```

Instala las bibliotecas npm de la IU de Google Material y las añade a las dependencias de los kits de inicio. Ahora puede utilizar los componentes de la IU de Material para procesar los componentes de formulario.


## &#x200B;2. Crear componentes React personalizados

Vamos a crear un componente personalizado que reemplace el componente [entrada de texto](https://spectrum.adobe.com/page/text-field/) predeterminado por el componente [Campo de texto de IU de Google Material](https://mui.com/material-ui/react-text-field/).

Se requiere un componente independiente para cada tipo de componente ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input) o `:type`) utilizado en una definición de formulario sin encabezado. Por ejemplo, en el formulario Contáctenos que creó en la sección anterior, los campos Nombre, Correo electrónico y Teléfono son de tipo `text-input` ([fieldType: &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def)) y el campo de mensaje es de tipo `multiline-input` ([&quot;fieldType&quot;: &quot;multiline-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/reference-json-properties-fieldtype--multiline-input)).


Vamos a crear un componente personalizado para superponer todos los campos de formulario que utilizan la propiedad [fieldType: &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def) con el componente [Campo de texto de IU de Material](https://mui.com/material-ui/react-text-field/).


Para crear el componente personalizado y asignar el componente personalizado con la propiedad [fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def):

1. Abra el directorio **react-starter-kit-aem-headless-forms** en un editor de códigos y vaya a `\react-starter-kit-aem-headless-forms\src\components`.


1. Cree una copia de la carpeta **`slider`** o **`richtext`** y cambie el nombre de la capeta copiada por **materialtextfield**. `slider` y `richtext` son dos componentes personalizados de muestra disponibles en la aplicación de inicio. Puede utilizarlos para crear sus propios componentes personalizados.

   ![El componente personalizado materialtextfield en VSCode](/help/assets/richtext-custom-component-in-vscode.png)

1. Abra el archivo `\react-starter-kit-aem-headless-forms\src\components\materialtextfield\index.tsx` y reemplace el código existente por el siguiente código. Este código devuelve y procesa un componente [Campo de texto de IU de Google Material](https://mui.com/material-ui/react-text-field/).

```JavaScript
 
     import React from 'react';
     import {useRuleEngine} from '@aemforms/af-react-renderer';
     import {FieldJson, State} from '@aemforms/af-core';
     import { TextField } from '@mui/material';
     import Box from '@mui/material/Box';
     import { richTextString } from '@aemforms/af-react-components';
     import Typography from '@mui/material/Typography';


     const MaterialtextField = function (props: State<FieldJson>) {

         const [state, handlers] = useRuleEngine(props);

         return(

         <Box>
             <Typography component="legend">{state.visible ? richTextString(state?.label?.value): ""} </Typography>
             <TextField variant="filled"/>
         </Box>

         )
     }

     export default MaterialtextField;
```


La parte `state.visible` comprueba si el componente está configurado para ser visible. Si es así, la etiqueta del campo se recupera y se muestra mediante `richTextString(state?.label?.value)`.

![](/help/assets/material-text-field.png)


Su componente personalizado `materialtextfield` está listo. Vamos a configurar este componente personalizado para reemplazar todas las instancias de [fieldType: &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def) por el campo de texto de la IU de Google Material.

## &#x200B;3. Asignar un componente personalizado con campos de formulario sin encabezado

El proceso de utilizar componentes de una biblioteca de terceros para procesar campos de formulario se conoce como asignación. Debe asignar cada ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input)) a un componente correspondiente de una biblioteca de terceros.

Toda la información relacionada con la asignación se añade al archivo `mappings.ts`. La instrucción `...mappings` del archivo `mappings.ts` hace referencia a las asignaciones predeterminadas, que se superponen a los componentes ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input) o `:type`) con [Adobe Spectrum](https://spectrum.adobe.com/page/text-field/).

Para añadir la asignación para el componente `materialtextfield`, creado en el último paso:

1. Abra el archivo `mappings.ts`.

1. Añada la siguiente instrucción de importación para incluir el componente `materialtextfield` al archivo `mappings.ts`:


   ```JavaScript
       import MaterialtextField from "../components/materialtextfield";
   ```

1. Añada la siguiente instrucción para asignar `text-input` con el componente materialtextfield.


   ```JavaScript
       "text-input": MaterialtextField
   ```

   El código final del archivo tiene el siguiente aspecto:

   ```JavaScript
         import { mappings } from "@aemforms/af-react-components";
         import MaterialtextField from "../components/materialtextfield";
   
   
         const customMappings: any = {
           ...mappings,
           "text-input": MaterialtextField
        };
        export default customMappings;
   ```

1. Guarde y ejecute la aplicación. Los tres primeros campos del formulario se representan mediante [Campo de texto de IU de Google Material](https://mui.com/material-ui/react-text-field/):

   ![](assets/material-text-field-form-rendetion.png)


   Del mismo modo, puede crear componentes personalizados para los campos de mensaje (&quot;fieldType&quot;: &quot;multiline-input&quot;) y clasificación del servicio (&quot;fieldType&quot;:&quot;number-input&quot;). Puede clonar el siguiente repositorio Git para los componentes personalizados de los campos de mensaje y clasificación del servicio:

   [https://github.com/singhkh/react-starter-kit-aem-headless-forms](https://github.com/singhkh/react-starter-kit-aem-headless-forms)

## Siguiente paso

Ha procesado correctamente el formulario con componentes personalizados que utilizan la IU de Google Material. ¿Ha intentado enviar el formulario haciendo clic en el botón Enviar (asignado con el componente de IU de Google Material correspondiente)? Si no, adelante. Inténtelo.

¿El formulario envía los datos a alguna fuente de datos? No? No se preocupe. Esto se debe a que el formulario no está configurado para comunicarse con la biblioteca en tiempo de ejecución.

¿Cómo puede configurar el formulario para comunicarse con ella? Próximamente se publicará un artículo que lo explica todo en detalle. Permanezca atento.
