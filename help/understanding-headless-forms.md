---
title: 'Explicación de los formularios sin encabezado: conceptos y preguntas frecuentes'
description: Respuestas a preguntas comunes sobre qué son los formularios sin encabezado, en qué se diferencian de las bibliotecas de formularios tradicionales, los detalles de implementación, el control de la interfaz de usuario, el rendimiento y la integración con marcos y back-ends.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: formularios sin encabezado, biblioteca de formularios sin encabezado, formularios adaptables, administración de estado, validación, sistema de diseño, SSR, CMS
hide: false
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '2605'
ht-degree: 5%

---


# Explicación de los formularios sin encabezado: conceptos y preguntas frecuentes {#understanding-headless-forms}

Esta guía responde a preguntas comunes sobre los formularios sin encabezado en general y cómo se aplican a AEM Headless Adaptive Forms. Utilícelo para decidir cuándo utilizar un enfoque sin encabezado y cómo implementar, aplicar estilos e integrar formularios en la pila.

## Conceptos básicos y comprensión {#basics-understanding}

### ¿Qué es exactamente una biblioteca de formularios sin encabezado?

Una **biblioteca de formularios sin encabezado** es una solución de formularios que separa **lógica de formulario** (estado, validación, reglas, envío) de **presentación** (componentes de interfaz de usuario y estilo). El &quot;encabezado&quot; es la interfaz de usuario del formulario visible; &quot;sin encabezado&quot; significa que la biblioteca no dicta ni envía una interfaz de usuario fija. En su lugar, expone:

* Un **modelo de formulario** (a menudo JSON): estructura, campos, restricciones y reglas.
* **API o enlaces** para leer y actualizar el estado del formulario, ejecutar la validación y controlar el envío.
* **Eventos y ciclo de vida** para que la interfaz de usuario pueda reaccionar a los cambios.

En Forms adaptable sin encabezado de AEM, el formulario es una [estructura JSON](architecture.md) alojada en Adobe Experience Manager. [Forms Web SDK](architecture.md#developer-tools) (tiempo de ejecución del lado del cliente) proporciona la capa lógica (procesador de reglas de negocio, administración de estado, validación) mientras que la aplicación proporciona la interfaz de usuario que procesa esa estructura.

### ¿En qué se diferencia un formulario sin encabezado de una biblioteca de formularios tradicional?

| Aspecto | Biblioteca de formularios tradicional | Biblioteca de formularios sin encabezado |
|--------|---------------------------|------------------------|
| **IU** | Se envía con componentes y estilos integrados | No hay una interfaz de usuario prescrita; puede traer sus propios componentes |
| **Estilo** | Tematización o invalidaciones en los componentes de la biblioteca | Control total; use su sistema de diseño tal cual |
| **Definición de formulario** | A menudo solo de código (componentes en JSX/HTML) | A menudo impulsado por datos (JSON/esquema de CMS o API) |
| **Estado y validación** | Vinculado a los componentes de la biblioteca | Expuesto a través de API/ganchos; cualquier interfaz de usuario puede enlazarse a ellos |
| **Canales** | Normalmente web (a veces un marco de trabajo) | La misma definición de formulario puede impulsar la web, el móvil, el chat, etc. |

Con AEM Headless Adaptive Forms, [crea y publica un formulario](create-and-publish-a-headless-form.md) una vez en AEM; cualquier cliente (React, Angular, móvil nativo, bot de chat) puede [recuperar el formulario JSON](architecture.md) y procesarlo con la interfaz de usuario adecuada para ese canal.

### ¿Por qué debería utilizar formularios sin encabezado en lugar de una solución de formulario basada en la interfaz de usuario?

Los formularios sin encabezado son adecuados cuando necesita:

* **Diseñe la coherencia del sistema**: utilice los componentes y la marca existentes sin combatir los valores predeterminados de la biblioteca.
* **Multicanal**: una definición de formulario para puntos de contacto web, móviles y de otro tipo (consulte [Información general](overview.md)).
* **Formularios impulsados por CMS o backend**: los autores cambian la estructura y las reglas de los formularios sin implementaciones de código; su aplicación solo consume el JSON.
* **Flexibilidad del marco de trabajo** - La biblioteca [AF-core](https://www.npmjs.com/package/@aemforms/af-core) es independiente del marco de trabajo; los enlaces de React se proporcionan por comodidad, pero puede generar enlaces para otros marcos de trabajo.
* **Funciones back-end**: aproveche AEM Forms para prerrellenar, validar, enviar, flujos de trabajo y modelos de datos de Forms sin bloquearse en una pila de IU específica.

### ¿Cuándo tiene sentido utilizar un enfoque sin encabezado?

Utilice formularios sin encabezado cuando:

* Tiene o desea un sistema de diseño o una biblioteca de componentes sólidos.
* Los usuarios que no son desarrolladores (por ejemplo, en un CMS) crean Forms, que debe funcionar en varias aplicaciones o canales.
* Necesita la misma lógica de formulario (validación, reglas) en la web, dispositivos móviles u otros clientes.
* Desea minimizar los nuevos procesamientos y mantener la lógica del formulario comprobable independientemente de la interfaz de usuario.

Considere una biblioteca de formularios tradicional incluida en la interfaz de usuario cuando:

* Necesita un formulario de trabajo en una sola aplicación web rápidamente y no le importa la interfaz de usuario personalizada o los canales múltiples.
* Su equipo prefiere definir formularios solo en código en un marco de trabajo.

### ¿Es &quot;sin encabezado&quot; solo una palabra de moda o resuelve problemas reales?

Soluciona problemas arquitectónicos reales:

* **Separación de preocupaciones**: la estructura de formulario, las reglas y la validación se encuentran en los datos y en una capa lógica; la capa de interfaz de usuario solo procesa y distribuye las acciones del usuario. Esto mejora la estabilidad y la reutilización.
* **Independencia del canal**: una definición de formulario puede controlar distintas interfaces de usuario (por ejemplo, React web, React Native, Angular o Voice). Los Forms adaptables sin encabezado de AEM se han creado para esto: [compilar una vez, entregar en React, SPA, web, móvil y más](overview.md).
* **Creación sin código**: los usuarios empresariales pueden cambiar campos y reglas en el [editor de formularios adaptables](create-a-headless-adaptive-form.md); los desarrolladores no necesitan volver a implementar para los cambios de contenido.
* **Integración con pilas existentes**: conserva su sistema de diseño, administración de estado y enrutamiento; la capa sin encabezado solo administra el estado de formulario, la validación y el envío.

## Implementación y preguntas técnicas {#implementation-technical}

### ¿Cómo administran el estado los formularios sin encabezado?

En Forms adaptable sin encabezado de AEM, el estado se administra mediante **Forms Web SDK**:

* **Procesador de reglas de negocios**: acepta el formulario JSON, administra el estado del campo y ejecuta las reglas y los controladores de eventos definidos en el JSON.
* **Enlazador React**: proporciona enlaces (por ejemplo, `useRuleEngine`) sobre el controlador para que los componentes React reciban el estado actual y los controladores; las IU que no sean React pueden consumir el mismo estado a través de las API principales.
* **Estado** incluye valores de campo, visibilidad, validez y cualquier propiedad personalizada definida en el modelo de formulario.

Los componentes de la interfaz de usuario reciben el estado y los controladores (por ejemplo, `[state, handlers] = useRuleEngine(props)`); usted procesa desde `state` y llama a `handlers` cuando el usuario interactúa. El motor en tiempo de ejecución mantiene el estado sincronizado con la definición y las reglas del formulario. Ver [Arquitectura](architecture.md) y [Usar componentes personalizados para procesar un formulario sin encabezado](developing-for-headless-forms-using-your-own-components.md).

### ¿Cómo funciona la validación en una configuración de formulario sin encabezado?

La validación forma parte de la capa de lógica del formulario:

* **Las restricciones** se definen en el formulario JSON (por ejemplo, obligatorio, mínimo/máximo, patrón). Forms Web SDK aplica estas restricciones y expone el estado de validación (por ejemplo, válido/no válido, mensajes de error) a los componentes.
* SDK aplica la **validación del lado del cliente** en función de la estructura del formulario; la interfaz de usuario muestra errores de estado.
* **La validación del lado del servidor** está disponible a través de las API de AEM (por ejemplo, validar extremo); puede validarla antes o durante el envío.

No implementa la lógica de validación en la interfaz de usuario, solo muestra el estado de validación y los mensajes proporcionados por el motor en tiempo de ejecución.

### ¿Puedo integrar formularios sin encabezado con la validación de esquemas (Yup, Zod, Joi)?

La validación integrada está impulsada por las restricciones JSON del formulario. Para usar Yup, Zod, Joi o similar:

* Puede **derivar o generar** el formulario adaptable sin encabezado JSON a partir de su esquema (por ejemplo, convertir el esquema JSON al formulario JSON) para que una fuente de verdad controle la validación del esquema y la estructura del formulario.
* Para **validación personalizada** más allá del formulario JSON, puede ejecutar sus propios validadores (Yup/Zod/Joi) en los controladores de eventos o antes de enviar e insertar los resultados en el estado del formulario o en el envío del bloque. Los puntos de integración son los mismos vínculos o API que utiliza para el estado y el envío.

La [especificación de Forms adaptable](/help/assets/headless-adaptive-forms-specification.pdf) y la [fórmula JSON](architecture.md) definen la regla y el modelo de restricción que usa el tiempo de ejecución.

### ¿Cómo gestiono la validación asíncrona (por ejemplo, la disponibilidad del nombre de usuario)?

La validación asíncrona se puede implementar en la capa de aplicación:

* Use **reglas o controladores de eventos** en el formulario JSON (donde sea compatible) para almacenar en déclencheur la lógica cuando cambie un campo.
* En sus **componentes personalizados**, use los mismos vínculos de estado/controlador para llamar a su backend (por ejemplo, la API de disponibilidad de nombre de usuario) y, a continuación, actualice la validez del campo o muestre un error a través de las API de tiempo de ejecución o el estado local que aparezca en la interfaz de usuario.
* Como alternativa, realice la comprobación **al desenfocar o antes de enviar** y establezca el estado del campo en no válido con un mensaje personalizado si la comprobación asincrónica falla.

El patrón exacto depende de cómo se integre la aplicación con el [procesador de reglas del negocio](architecture.md) y los componentes personalizados.

### ¿Cómo envío datos a las API mediante formularios sin encabezado?

El envío está disociado de la interfaz de usuario:

* **Acciones de envío de AEM**: configure el formulario en AEM para enviarlo a puntos de conexión REST, correo electrónico o integraciones (como Microsoft Dynamics, Salesforce). El formulario se envía a través de AEM, que administra la llamada real HTTP/backend. Ver [Usar eventos para controlar y enviar datos de formulario](use-events-to-handle-and-submit-form-data.md).
* **Envío del lado del cliente**: su aplicación puede escuchar el envío o recopilar datos de formulario del estado de tiempo de ejecución y enviarlos a sus propias API. Las [API HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) enumeran, recuperan, validan, envían y rastrean el estado de envío.
* **Relleno previo**: los datos se pueden rellenar previamente a través de puntos de conexión REST o del lado del servidor para que cuando se cargue el formulario, el estado ya se rellene. Ver [Storybook - ejemplo de relleno previo](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data).

## Control de diseño e interfaz de usuario {#ui-design-control}

### ¿Puedo utilizar mi propio sistema de diseño o biblioteca de componentes con formularios sin encabezado?

Sí. Esta es una ventaja central de los formularios sin encabezado. Con Forms adaptable sin encabezado de AEM:

* Ha **asignado** sus propios componentes al modelo de formulario (por tipo de campo o tipo de recurso). Vea [Usar componentes personalizados para procesar un formulario sin encabezado](developing-for-headless-forms-using-your-own-components.md) y [Usar componentes React de la interfaz de usuario de Google Material para procesar un formulario sin encabezado](use-google-material-ui-react-components-to-render-a-headless-form.md).
* El motor en tiempo de ejecución proporciona **estado y controladores**; los componentes se procesan con el sistema de diseño y llaman a los controladores para que la lógica del formulario permanezca sincronizada.
* Puede usar **React Spectrum**, la interfaz de usuario de material, la interfaz de usuario de Chakra o cualquier biblioteca de componentes personalizada; la [especificación](/help/assets/headless-adaptive-forms-specification.pdf) se puede ampliar para componentes personalizados (por ejemplo, la interfaz de usuario de Chakra, Vue.js). Ver [preguntas más frecuentes - marcos personalizados](faq.md#is-it-possible-to-use-headless-adaptive-forms-with-custom-frameworks).

### ¿Los formularios sin encabezado son compatibles con la accesibilidad (ARIA, administración del teclado)?

La accesibilidad está implementada en la **capa de interfaz de usuario** que proporciona. La capa sin encabezado no procesa DOM, por lo que no agrega ningún comportamiento ARIA o de teclado por sí misma. La accesibilidad se obtiene de las siguientes formas:

* Usando **componentes accesibles** desde su sistema de diseño o biblioteca (muchos incluyen compatibilidad con ARIA y teclado).
* Siguiendo **prácticas recomendadas de accesibilidad** en los componentes de campo personalizado (etiquetas, mensajes de error, administración del enfoque, navegación mediante el teclado).
* Garantizar que la estructura y el estado del formulario que reciba (por ejemplo, obligatorio, no válido y visible) se reflejen en los atributos y el comportamiento de ARIA de los componentes.

Si utiliza los componentes basados en React Spectrum predeterminados, se beneficiará de su accesibilidad integrada.

### ¿Cómo administro componentes de interfaz de usuario complejos (selectores de fechas, desplegables personalizados)?

Trátelos como **componentes personalizados** asignados a los tipos de campo o tipos de recursos personalizados correspondientes en el formulario JSON:

* Implemente su componente para aceptar las mismas **propiedades/estado/controladores** que otros componentes de campo (por ejemplo, a través de `useRuleEngine`).
* Use **estado** para el valor, la visibilidad y la validez; use **controladores** para actualizar la validación del valor y el déclencheur.
* Procese el selector de fechas o el menú desplegable personalizado con la biblioteca de IU elegida; al cambiar, llame al controlador con el nuevo valor para que el estado del formulario permanezca correcto.

Vea [Usar componentes personalizados para procesar un formulario sin encabezado](developing-for-headless-forms-using-your-own-components.md) para su asignación por tipo de campo y tipo de recurso.

### ¿Se pueden agregar o quitar campos (formularios dinámicos) de forma dinámica?

La estructura del formulario está definida por el **formulario JSON** devuelto desde el servidor. El comportamiento dinámico se logra mediante:

* **Reglas con el formato JSON**: mostrar/ocultar, habilitar/deshabilitar o establecer valores basados en expresiones. El [procesador de reglas de negocio](architecture.md) ejecuta estas reglas; sus componentes reaccionan a `state.visible` y similares.
* **Estructura controlada por el servidor**: distintos usuarios o contextos pueden recibir formularios JSON diferentes (por ejemplo, pasos o secciones diferentes), por lo que &quot;dinámico&quot; puede significar &quot;definición de formulario diferente por solicitud&quot;.
* **Cambios del lado del cliente**: si su aplicación puede modificar el modelo de formulario (por ejemplo, agregar o quitar elementos en una estructura repetible), el tiempo de ejecución puede reflejarlo; la capacidad exacta depende del esquema de formulario y de las API de tiempo de ejecución.

[Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) incluye ejemplos de comportamiento dinámico.

### ¿Cómo administro los campos condicionales (mostrar/ocultar en función de la entrada)?

La visibilidad condicional está controlada por **rules** con el formato JSON, evaluadas por el procesador de reglas del negocio. Usted define condiciones (por ejemplo, &quot;cuando el campo A es igual a X, mostrar campo B&quot;); el tiempo de ejecución actualiza el estado (por ejemplo, `state.visible`). Los componentes solo necesitan **respetar el estado** (por ejemplo, `if (!state.visible) return null;`). No se requiere ninguna lógica de interfaz de usuario adicional para mostrar u ocultar más allá del procesamiento desde el estado. El comportamiento en cascada y condicional está documentado en la [especificación de Forms adaptable](/help/assets/headless-adaptive-forms-specification.pdf) y se muestra en [Storybook - campos en cascada](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down). Vea también [preguntas más frecuentes - campos en cascada](faq.md#do-headless-adaptive-forms-support-cascading-fields).

## Rendimiento y escalabilidad {#performance-scalability}

### ¿Los formularios sin encabezado son más eficaces que las bibliotecas de formularios tradicionales?

Pueden serlo, pero depende de la implementación:

* **Actualizaciones dirigidas**: un tiempo de ejecución sin encabezado bien diseñado actualiza solo el estado que ha cambiado y notifica únicamente a los componentes que dependen de él, lo que puede reducir los renderizamientos innecesarios en comparación con un componente de formulario monolítico.
* **Paquete de IU más pequeño**: solo se envían los componentes de la IU que se usan (el sistema de diseño), no un conjunto completo de componentes de la biblioteca.
* **Carga diferida**: se puede recuperar el JSON del formulario cuando se necesite; el paquete inicial puede permanecer más pequeño.

El rendimiento también depende de cómo implemente los componentes (por ejemplo, evitando representaciones y memorias innecesarias).

### ¿Cómo minimizan las renderizaciones?

* **Forma de estado**: el motor en tiempo de ejecución mantiene el estado de formulario en una estructura que permite actualizaciones específicas, de modo que sólo las partes afectadas del árbol necesitan volver a procesarse.
* **Diseño de vínculos**: los vínculos como `useRuleEngine` se pueden implementar para suscribir componentes únicamente al estado que utilizan, de modo que los cambios principales o del mismo nivel no obliguen a que se vuelva a procesar cada campo.
* **Su responsabilidad**: puede minimizar aún más los nuevos procesamientos mediante las prácticas recomendadas de React (por ejemplo, `React.memo`, devoluciones de llamadas estables) en sus componentes personalizados.

### ¿Los formularios sin encabezado se adaptan bien a los formularios grandes de varios pasos?

Sí, cuando está diseñado correctamente:

* **Definición de formulario**: los formularios grandes se pueden dividir en pasos o secciones en el JSON; es posible que solo el paso o la sección visible deban estar completamente activos en la interfaz de usuario, con evaluación diferida de las reglas para secciones ocultas si se admite.
* **Estado**: el motor en tiempo de ejecución contiene un estado de formulario coherente; la navegación por pasos solo muestra u oculta secciones o actualiza el &quot;paso actual&quot; sin duplicar datos.
* **Fragmento y carga diferida**: puede recuperar el JSON de un fragmento o cargar secciones adicionales con un paso por adelantado para mantener la carga útil inicial y el coste de análisis bajos.

Para los formularios muy grandes, considere la estructura (por ejemplo, pasos del asistente), las variantes de formulario impulsadas por el servidor y la medición del procesamiento y la ejecución de reglas con cargas útiles reales.

## Integración y ecosistema {#integration-ecosystem}

### ¿Pueden los formularios sin encabezado funcionar con las acciones Next.js, SSR y servidor?

* **Next.js / React** - Sí. El procesador y los enlaces de React funcionan en un entorno de React. Utilice Forms Web SDK en los componentes del cliente; obtenga el formulario JSON en el servidor o cliente según sea necesario.
* **SSR**: puede recuperar el formulario JSON en el servidor y pasarlo al cliente para que el formulario se hidrate con datos. La interactividad de formularios (estado, validación, reglas) se ejecuta en el cliente donde se carga SDK. Evite procesar campos de formulario que dependan del estado solo de cliente durante la SR o utilice un marcador de posición que se hidrate en el cliente.
* **Acciones del servidor (Next.js)**: puede llamar a Acciones del servidor desde el controlador de envío: cuando el usuario envía, el código de cliente recopila datos de formulario (desde el estado sin encabezado) y llama a una Acción del servidor en lugar de o además de los extremos de envío de AEM.

### ¿Cómo se integran los formularios sin encabezado con CMS, el comercio sin encabezado o los sistemas back-end?

* **CMS**: AEM es el CMS para la definición del formulario: los autores crean y publican el formulario JSON. Otros CMS pueden hacer referencia al formulario, la URL o la API o vincularlo a él. La aplicación recupera el formulario de AEM (o una CDN) y, opcionalmente, extrae una copia o un diseño de otro CMS.
* **Rellenar previamente y enviar** - [Rellenar previamente](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) y enviar pueden llegar a los extremos de REST, por lo que puede rellenar previamente desde un back-end de CRM, DAM o comercio y enviarlo al mismo sistema o a sistemas diferentes. AEM Forms también admite [Microsoft Dynamics y Salesforce](faq.md), REST, correo electrónico y acciones de envío personalizadas.
* **Modelo de datos de Forms**: AEM Forms proporciona un modelo de datos de Forms para conectarse a fuentes de datos diferentes; los formularios sin encabezado pueden utilizar estas capacidades para el relleno previo, la validación y el envío sin que usted mismo genere cada integración.

En los escenarios móviles y sin conexión, el enfoque recomendado es [crear su propia aplicación y recuperar las definiciones de los formularios a través de la API de Forms adaptable sin encabezado](mobile-forms-best-practices.md).

## Consulte también {#see-also}

* [Información general](overview.md)
* [Arquitectura](architecture.md)
* [Preguntas frecuentes](faq.md)
* [Creación y publicación de un formulario sin encabezado](create-and-publish-a-headless-form.md)
* [API de formularios adaptables sin encabezado](https://opensource.adobe.com/aem-forms-af-runtime/api/)
* [Zona de juegos de códigos](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=es)
* [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)
