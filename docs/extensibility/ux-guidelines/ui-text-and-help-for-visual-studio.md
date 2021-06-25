---
title: Texto de la interfaz de usuario y Ayuda para Visual Studio | Microsoft Docs
description: Obtenga información sobre el texto de la interfaz de usuario y la terminología que se usa en la información de ayuda para Visual Studio.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40b128c5e95c70457d92843e620b4aa072c409ba
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899438"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Texto de la interfaz de usuario y ayuda para Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a> Texto y terminología de la interfaz de usuario
 El texto comprensible es fundamental para una interfaz de usuario eficaz. Los usuarios de software tienden a leer primero las etiquetas, es decir, las más relevantes para completar la tarea en cuestión. El texto estático se lee con menos frecuencia. Planee que los usuarios inicien sus sesiones de trabajo con un examen rápido de toda la ventana, seguido de una lectura de la interfaz de usuario en este orden aproximado:

1. Controles interactivos en el centro

2. Botones de confirmación

3. Controles interactivos encontrados en otra parte

4. Instrucciones principales

5. Explicaciones complementarias

6. Título de la ventana

7. Otro texto estático en el cuerpo principal

### <a name="usage-patterns-for-ui-text"></a>Patrones de uso para el texto de la interfaz de usuario

#### <a name="title-bar-text"></a>Texto de la barra de título
 El texto de la barra de título debe coincidir con el comando que generó la interfaz de usuario.

#### <a name="instructional-text-helper-text"></a>Texto informativo (texto auxiliar)
 En algunos diálogos, resulta útil proporcionar instrucciones principales destacadas para explicar qué hacer en la ventana o en la página. Esto se conoce a veces como "texto auxiliar".

##### <a name="writing-style-rules-for-helper-text"></a>Escribir reglas de estilo para el texto auxiliar

- No explique lo obvio. A menos que sea absolutamente necesario, no incluya texto informativo.

- El texto informativo siempre se coloca en la parte superior del cuadro de diálogo y debe hacer referencia a la tarea que se está realizando.

- Explicar con precisión a los usuarios lo que necesitan hacer. Evite una comunicación y redundancia excesivas.

- Revise cada ventana y elimine palabras e instrucciones duplicadas.

- Mantenga el texto informativo corto. Si se necesita más información para determinados usuarios o escenarios, proporcione un vínculo a un tema conceptual en línea detallado.

- Escriba el texto para que cada palabra mantenga el peso y sea necesario.

- Siga las instrucciones existentes de Microsoft [Interfaz de usuario texto y](/windows/desktop/uxguide/text-ui) estilo y [tono.](/windows/desktop/uxguide/text-style-tone)

#### <a name="supplemental-instructions"></a>Instrucciones complementarias
 Las instrucciones complementarias proporcionan información adicional que ayuda al usuario a comprender los controles o las agrupaciones de controles. Esto también podría incluir el texto de sugerencia necesario para comprender qué formato espera el control de entrada. Use instrucciones complementarias con moderación. Reservarlos para los casos en los que es probable que el usuario no comprenda completamente las ramificaciones de la elección que está realizando.

 ![Captura de pantalla que muestra Internet Explorer opciones con texto complementario debajo que describe el impacto de cambiar la configuración de la opción.](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Texto complementario en Visual Studio**

 ![Captura de pantalla del cuadro de diálogo Elegir control de código fuente Visual Studio texto complementario que describe cada una de las opciones del sistema de control de código fuente.](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Texto complementario en Visual Studio**

#### <a name="infotips"></a>Información sobre información
 A menudo, el texto informativo puede ser demasiado largo para colocarse en la interfaz de usuario o puede ser útil solo para los nuevos usuarios, con sentimiento de desorden para los usuarios experimentados. En este caso, el texto informativo o informativo debe colocarse como información sobre herramientas en una información sobre herramientas.

 La información sobre información debe colocarse cerca de los controles con los que están relacionados y debe usar el icono de información específica, que es discreto pero evidente.

 ![Panel informativo en Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Ejemplo de información sobre información en Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Escribir reglas de estilo para información sobre información

- Escriba información sobre información como oraciones completas. Requieren verbos específicos, mayúsculas y minúsculas de oración y puntuación final.

- Use Información sobre información para complementar su instrucción o información principal. Si solo usa palabras diferentes para volver a establecer la idea principal, no necesita información.

- Mantenga infoTips corto y tierno. Use palabras pequeñas y un lenguaje sencillo y cotidiano que admita y fomente al usuario.

- Siga las instrucciones existentes de Microsoft [Interfaz de usuario texto y](/windows/desktop/uxguide/text-ui) estilo y [tono.](/windows/desktop/uxguide/text-style-tone)

#### <a name="control-labels"></a>Etiquetas de control
 Las etiquetas de control deben ser cortas, concisas y seguir las instrucciones [de escritorio de Windows para Controles](/windows/desktop/uxguide/controls).

 Para obtener más información sobre el formato de etiqueta de control y la ubicación dentro de la interfaz de usuario, consulte [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Vínculos a la Ayuda
 Los vínculos de ayuda se pueden colocar en texto informativo o en el cuerpo de la interfaz de usuario. Pueden ser vínculos a la Ayuda o iniciar diálogos internos.

##### <a name="visual-style-rules-for-help-links"></a>Reglas de estilo visual para vínculos de Ayuda

- Use los colores de entorno correctos para los hipervínculos. Un hipervínculo con el estilo correcto no parpadeará brevemente en rojo cuando se haga clic en él. Si ve esto, es una indicación de que no se usan colores de entorno.

- Los subrayados solo se deben usar al mantener el puntero o cuando el vínculo está incrustado en un párrafo.

- Para obtener información más detallada sobre los estilos visuales y de interacción para hipervínculos, vea Botones e hipervínculos.

##### <a name="writing-style-rules-for-help-links"></a>Escribir reglas de estilo para vínculos de Ayuda

- Al iniciar diálogos, mantenga los estándares de puntos suspensivos: sin puntos suspensivos para la navegación, puntos suspensivos si la tarea requiere interfaz de usuario adicional.

     ![Vínculo de ayuda en Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Un botón de puntos suspensivos (...) en un vínculo de Ayuda indica que la tarea requerirá una interfaz de usuario adicional.**

- Los vínculos no deben empezar por "Learn", ya que esa no es la intención del usuario. El usuario quiere responder a una pregunta específica, no recibir una educación general.

- Vínculos de ayuda de frases para que se haga la pregunta que el tema responderá.

     Incorrecto: "Más información sobre los precios de Windows Azure Mobile Services"

     Correcto: "¿Qué opciones de precios están disponibles para Windows Azure Mobile Services?"

- No use *nunca Haga clic...* en el texto del vínculo.

- Nunca vincule solo la palabra "aquí". Esto es problemático para algunos lectores de pantalla, que solo darán voz a la palabra con hipervínculo.

     Incorrecto: "Buscar información sobre Windows Azure Mobile Services **aquí"**

     Correcto: "¿Qué opciones de precios están disponibles para Windows Azure Mobile Services?"

- Para obtener más información sobre el estilo de escritura correcto para los vínculos de Ayuda, vea la guía [de escritorio de Windows para ayuda](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Texto de sugerencia
 El texto de la sugerencia aparece como una marca de agua dentro de un control o debajo del control. El formato correcto se aplicará mediante el token de VSColors adecuado, `Environment.GrayText` .

 Puede aparecer en una serie de formularios.

- En lugar de la etiqueta de control:

     ![Captura de pantalla de un control desplegable con texto de sugerencia en lugar de la etiqueta de control que dice "Buscar Explorador de soluciones (Ctrl+;)".](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Con un verbo, dando instrucciones:

     ![Captura de pantalla de un cuadro de texto con texto de sugerencia en el control que dice "Escriba su nombre".](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Con texto que indica una entrada obligatoria:

     ![Captura de pantalla de un cuadro de texto con texto de sugerencia en el control que dice \< \> "Obligatorio".](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Texto de marca de agua
 En una superficie de diseño vacía, el texto debe indicar qué hacer, así como proporcionar vínculos para abrir otras ventanas relacionadas, si procede:

 ![Texto de marca de agua en Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Ejemplo de texto de marca de agua en Visual Studio**

### <a name="common-terminology"></a>Terminología común

|Término|Explicación|Comentario|
|----------|-----------------|-------------|
|Inicio de sesión/Cerrar sesión|Verbos usados como sinónimos de la web para representar la autenticación en una propiedad web. Dentro de los clientes, usamos esto una vez como noción de nivel superior para iniciar y salir de la conexión de usuario ide, que representa una identidad de nivel superior que proporciona funcionalidades de nivel superior, como la itinerancia y las licencias que no están disponibles con todas las demás conexiones.|El usuario del IDE es la única característica que debe representar un verbo de inicio o de sesión, ya que representa al usuario del IDE de nivel superior.|
|Conexión/desconexión|Se usa en lugares donde una característica mantiene una conexión única a un servicio en línea.|Explorador de servidores, donde solo puede tener una conexión de Azure activa a la vez, es un ejemplo de conexión/desconexión.|
|Agregar o quitar|No destructivo. Use al agregar o quitar algo de una lista.|El cuadro de diálogo Connection Manager lista de servidores de TFS es un ejemplo de Agregar o quitar.|
|Eliminar|Destructivo. Use solo cuando el elemento que se va a quitar se descartará o eliminará permanentemente del disco.|Por lo general, "Eliminar" requiere un mensaje si el resultado elimina un archivo del disco.|

## <a name="error-messages"></a>Mensajes de error

### <a name="overview"></a>Información general
 Se producen errores. Establecer limitaciones en lo que el usuario puede hacer es un primer paso razonable para evitar mensajes de error evitables. Sin embargo, cuando se produce un error, un mensaje de error bien escrito puede avanzar mucho hacia la mitigación del problema. Los mensajes de error son posiblemente uno de los tipos de notificación más importantes que ve el usuario, ya que son sincrónicos e indican un problema que debe resolverse. Los mensajes de error mal escritos dejan a los usuarios por su cuenta para decidir la causa de los errores y las posibles soluciones.

 Los usuarios podrían dejar de prestar atención a los mensajes de error sobreutilizados o confusos, así que escriba solo los mensajes necesarios que agreguen valor a la experiencia del usuario. Si el mensaje es simplemente una notificación, use una presentación alternativa.

### <a name="rules-for-creating-an-error-message"></a>Reglas para crear un mensaje de error

- Al construir mensajes de error, elija el nivel de error adecuado para la audiencia. Tenga como objetivo resúmenes sencillos que proporcionen una acción que el usuario pueda realizar, si procede. No debe decir nada que el usuario no necesite saber.

- Proporcionar asistencia sanitaria. Es más fácil leer y actuar sobre un mensaje de error que contiene instrucciones.

- No use valores negativos dobles.

- Realice una gramática automatizada y manual y una comprobación ortográfica en cualquier mensaje de error que escriba.

- Para los mensajes de error complejos, evite las comunicaciones secuenciales. No use nunca un enlace F1 para el mensaje de error. El propio mensaje debe ser suficiente.

- Use el icono correcto.

- Facilitar la información y el uso de botones que tengan opciones claras, como "Eliminar" y "Cancelar".

- En el caso de las advertencias, tenga claro cuál será la consecuencia de continuar. Los botones deben indicar la consecuencia.

- En el caso de los errores, describa lo que el usuario puede hacer para corregir el problema. Los botones deben ser acciones o decir "Cerrar". No use un botón "Aceptar" para un mensaje de error.

- Algunas preguntas que debe hacer al crear un mensaje de error:

  - ¿Puede el usuario averiguar cómo resolver el problema solo con este error?

  - ¿El usuario usa el mismo vocabulario que este error?

  - ¿Este error es ambiguo o se comparte en varias situaciones? Si es así, ¿cómo guiar a los usuarios a la solución que necesitan?

#### <a name="build-errors"></a>Errores de compilación
 Puesto Visual Studio es una herramienta de desarrollo de software, muchos de sus componentes tienen un paso de compilación, conversión o codificación para convertir el trabajo del desarrollador en formato binario. Estas conversiones pueden producir errores cuando el compilador no puede procesar archivos creados incorrectamente o cuando las opciones del compilador no se han establecido correctamente.

 Visual Studio usuarios pueden dedicar un gran número de horas de desarrollo a resolver errores de compilación. Este tiempo de resolución aumenta cuando los errores tienen dependencias o cuando los mensajes de error están mal escritos, lo que puede dificultar el descubrimiento del origen del error.

 Los mejores errores de compilación son los que no se producen en primer lugar, por lo que Visual Studio proporciona los ondulados autocompletar e IntelliSense. Los validadores de esquema y herramientas similares proporcionan el mismo tipo de comentarios. Estos mecanismos guían al usuario de forma proactiva para construir código bien formado, lo que permite reducir la posibilidad de errores de compilación.

 Visual Studio proporciona una ventana de herramientas en la que los usuarios pueden leer y navegar por los errores que se produjeron en sus ventanas de documentos. Se proporcionan métodos abreviados de teclado para que el usuario pueda navegar rápidamente por grandes cantidades de código e ir directamente a la ubicación del problema. Visual Studio permite que cada error de compilación esté vinculado a un identificador de contexto o palabra clave de Ayuda determinado para que el usuario pueda ir directamente a un tema de Ayuda que proporciona información más detallada sobre el error.

 Escriba errores de compilación claros y concisos:

- **Use lenguaje sin formato** que explique el problema con poca o ninguna jerga del compilador. El texto de un error de compilación no debe ser muy técnico.

- **Describir las posibles causas.** Por ejemplo, "Falta un signo de dos puntos entre la propiedad y el valor en la declaración '(property) : (value)'".

- Proporcionar detalles sobre posibles correcciones. Si no hay suficiente espacio, se pueden incluir detalles adicionales en el tema de Ayuda correspondiente.

### <a name="components-of-a-well-written-error-message"></a>Componentes de un mensaje de error bien escrito

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Use el servicio de diálogo de shell para los mensajes de error.
 El uso del servicio de diálogo de shell le permite controlar la apariencia del mensaje, las fuentes en particular, sin cambios importantes en los elementos individuales. Use los **mecanismos IErrorInfo** y informe de ellos **mediante IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Elija una presentación de notificación eficaz y adecuada.
 Use un cuadro de diálogo modal con una advertencia crítica si se requiere una acción inmediata para evitar la pérdida de datos (notificación sincrónica). Los iconos críticos están reservados para situaciones en las que cerrar el mensaje sin leerlo puede provocar consecuencias negativas. La pérdida de datos es una situación crítica que requiere una respuesta de nivel de alarma. El uso excesivo del icono crítico hace que los usuarios no se desensistan de su importancia. Si el mensaje de error es informativo por naturaleza, considere alternativas a un diálogo modal (notificación asincrónica).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Proporcione una explicación clara y concisa de por qué se produjo el problema en lugar de una explicación técnica.
 Sobrecargar a los usuarios con detalles técnicos en la explicación hará que sea más probable que omitan los mensajes de error. Ejemplos de buena mensajería:

- "No se puede abrir el archivo solicitado".

- "No se puede conectar a Internet".

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Proporcione información sobre cómo corregir el problema.
 Ofrezca sugerencias al usuario sobre cómo corregir el problema. Sea leal con el usuario si no hay ninguna sugerencia. Proporcione vínculos directos a orígenes en línea alternativos, como soporte técnico o soporte técnico de la comunidad. Intente que los usuarios apunten a información en línea específica relacionada con el problema. Para obtener un identificador de error, considere la posibilidad de vincular usuarios a un subproceso de discusión sobre ese error específico. Ejemplos de buena mensajería:

- "Asegúrese de que está conectado a Internet y vuelva a intentar esta operación".

- "Asegúrese de que el archivo existe y de que tiene permiso para abrirlo".

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Escriba un mensaje que sea corto y hasta el punto.
 Un mensaje de error puede notificar, explicar y ofrecer una solución, pero seguir omitido si es demasiado wordy. Una solución es usar la divulgación progresiva con un botón de detalles. Por ejemplo, dé una breve descripción o solución y, a continuación, coloque más detalles en un botón de detalles. Si los usuarios deciden leer más información sobre el error, pueden hacerlo.

 El idioma del mensaje debe ser:

- **Adecuado para el dominio.** Use el lenguaje que el usuario comprenderá. Aunque nuestros clientes son desarrolladores, a menudo no tienen el contexto y la terminología que tenemos.

- **Específico.** Evite palabras imprecisas y dé nombres y ubicaciones específicos de los objetos implicados. Por ejemplo, un mensaje de error como "el carácter no es válido" no es útil. ¿Qué carácter? "No se encontró el archivo". ¿Qué archivo?

- **Cortés.** No culpe al usuario ni haga que se sienta cómodo. Evite el lenguaje ofensivo o ofensivo (kill, execute, terminate, fatal, illegal). Evite el texto en mayúsculas, que a menudo se ve como desenlazado y no es tan legible. No use el inglés.

- **Correcto.** Use la ortografía y gramática correctas (incluso en alfas). Los errores tipográficos son poco profesionales y embarazosos.

- **Contextualmente adecuado.** Use el texto del botón adecuado. Evite el botón "Aceptar" y, en su lugar, use "Continuar" o "Sí/No".

### <a name="error-message-examples"></a>Ejemplos de mensajes de error

|Bueno|Incorrecto|
|----------|---------|
|"El número que ha marcado ya no está en servicio. Compruebe el número y vuelva a marcar o marque 0 para el operador".|- "Error (449): número no es así"<br />- "Este error de excepción no controlada indica que la operación se completó correctamente".<br /><br /> ![Mensaje de error incorrecto en Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Obtener acceso a la Ayuda

### <a name="overview"></a>Información general
 Además de la documentación de MSDN, un Visual Studio cuenta con varios puntos de acceso para ayudar al usuario mientras está en la interfaz de usuario. Para asegurarse de que estos puntos de acceso están disponibles de forma coherente, los equipos de características deben aprovechar el sistema de ayuda que ofrece el entorno. Estos puntos de acceso son:

- **Texto informativo y complementario en diálogos.** Texto estático que proporciona dirección o explicación, ya sea en la superficie de la interfaz de usuario o disponible al mantener el puntero sobre un icono de información.

- **Ayuda F1** (solo editor). En el editor Visual Studio, un usuario puede confiar en que, en cualquier momento, al presionar F1 se mostrará un tema de Ayuda específico de la selección actual. Asegúrese de que los temas asociados a F1 sean adecuados e informativos.

- **Hipervínculos a temas de Ayuda.** Hipervínculo dentro de un cuadro de diálogo, ventana de herramientas o superficie de diseño que inicia un tema para ayudar al usuario a obtener más información sobre una tecnología, funcionalidad o información sobre cómo realizar una tarea.

- **Mecanismos de interfaz de usuario del asistente, como etiquetas inteligentes y cuadros de diálogo de creación.** Estos mecanismos ayudan al usuario a comprender un elemento de la interfaz de usuario o facilitan una tarea, como etiquetas inteligentes o diálogos de generador.

- **Botones de ayuda de la interfaz** de usuario (en desuso). Un indicador visible en la barra de título que proporciona acceso al tema de Ayuda F1 relacionado.

### <a name="text"></a>Texto

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Texto informativo y complementario en diálogos
 En los diálogos que admiten tareas complejas, es posible que sea necesario proporcionar texto informativo dentro de la interfaz de usuario, a menudo en la parte superior del diálogo o en controles casi complejos. Consulte El [texto de la interfaz de usuario y la terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obtener más información sobre el estilo de escritura.

#### <a name="infotips"></a>Información sobre información
 A menudo, el texto informativo puede ser demasiado largo para colocarse en la interfaz de usuario o puede ser útil solo para los nuevos usuarios, sintiéndose desordenado para los usuarios experimentados. En este caso, el texto informativo o informativo debe colocarse como información sobre herramientas en una información sobre herramientas.

 La información sobre información debe colocarse cerca de los controles con los que están relacionados y debe usar el icono de información específica, que es discreto pero evidente.

 ![Panel informativo en Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Ejemplo de información sobre información en Visual Studio**

### <a name="interactive-help-mechanisms"></a>Mecanismos interactivos de ayuda

#### <a name="f1-help"></a>Ayuda F1
 La Ayuda F1 es necesaria dentro de un editor o una superficie de diseño, pero no en ningún otro lugar del Visual Studio diseño.

#### <a name="hyperlinks-to-help-topics"></a>Hipervínculos a temas de Ayuda
 Los hipervínculos se pueden usar para realizar una acción, navegar dentro del IDE o iniciar la Ayuda en un explorador. Consulte [Texto y terminología de la](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) interfaz de usuario para obtener más información sobre el idioma y los botones e hipervínculos de 07.10.01 para obtener instrucciones visuales y de diseño.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Botones de ayuda [?] en las barras de título del cuadro de diálogo (en desuso)
 En su mayor parte, los botones ayuda [?] de la barra de título de los diálogos están en desuso. Los temas de la interfaz de usuario ya no forman parte de nuestro modelo de documentos y, por tanto, es posible que no haya un tema pertinente al que vincular. Básicamente, el botón de la barra de título era lo mismo que la Ayuda F1 y eso ya no es necesario en los diálogos. En algunos casos, esto todavía se puede usar como indicador de que hay más información conceptual o de procedimientos disponible, aunque los hipervínculos se usan con más frecuencia en la interfaz de usuario más reciente.

##### <a name="dialogs-created-through-the-environment"></a>Cuadros de diálogo creados a través del entorno
 Muchos diálogos de shell se crean mediante **la función VBDialogBoxParam.** Esta función compartida se actualizó para ayudar a mover el **botón Ayuda** del cuadro de diálogo a **?** mientras se conserva una arquitectura compatible con versiones anteriores y extensible.

 En concreto, la función **VBDialogBoxParam** busca en la plantilla de cuadro de diálogo un botón cuyo identificador es **IDHELP** (9) o etiqueta es **Help** o **&Help**. Si se encuentra un botón Ayuda,  se oculta y el WS_EX_CONTEXTHELP se agrega al cuadro de diálogo, que coloca **el elemento ?** en la barra de título del cuadro de diálogo.

 Cuando se crea el diálogo, inserta el procedimiento de diálogo en una pila e invoca el diálogo con un procedimiento de diálogo de procesamiento previo denominado **DialogPreProc**. Cuando **el ?** se hace clic en él, se envía **una** WM_SYSCOMMAND de **SC_CONTEXTHELP** al cuadro de diálogo. **DialogPreProc captura** este comando y lo cambia **a** un mensaje WM_HELP, que se pasa al procedimiento de diálogo original.

 La mayoría de los diálogos creados por el entorno tienen un botón Ayuda en el cuadro de diálogo. Cuando se muestra el cuadro de diálogo, el botón Ayuda se oculta automáticamente y solo el **elemento ?** funciona. Si **el ?** el botón se quita o cambia en Windows, esta solución le permite volver rápidamente a los botones de Ayuda originales.

 Esta solución realiza cuatro suposiciones que podrían provocar errores:

- El botón de ayuda del cuadro de diálogo **es IDHELP** (9).

- El cuadro de diálogo tiene el aspecto correcto cuando el botón Ayuda está oculto.

- El cuadro de diálogo no sustituye a su winproc.

- El diálogo no se incrusta dentro de otro diálogo.

  Si el cuadro de diálogo reside en msenv y no usa **VBDialogBoxParam,** investigue el aprovechamiento de **VBDialogBoxParam** antes de implementar su propio controlador.

##### <a name="dialogs-created-through-other-packages"></a>Cuadros de diálogo creados a través de otros paquetes
 Puede implementar su propia solución para los diálogos que residen fuera de msenv. Para una clase de diálogo compartido en el VSPackage, considere la posibilidad de mover el botón a la barra de título o implementar un controlador en cada diálogo. El código siguiente es un esqueleto de una implementación que le ayudará a empezar a trabajar:

```
struct DLGPROCITEM
{
    FARPROC proc; // The info used to create the dialog.
    DLGPROCITEM* procPrev;
};

DLGPROCITEM* g_dlgProcStack = NULL;

// A dialog starter/wrapper function is used to push the new
// dialog proc to the top of our dialog proc stack.

int SomeDialogStarterFunction(hinst, id, proc, etc)
{
    if (g_dlgProcStack == NULL)
    {
        g_dlgProcStack = new DLGPROCITEM;
        g_dlgProcStack->procPrev = NULL;
    }
    else
    {
        DLGPROCITEM* procItem = new DLGPROCITEM;
        g_dlgProcStack->procPrev = g_dlgProcStack;
        g_dlgProcStack = procItem;
    }
}

// Pop this dialog proc off the dialog proc stack.

DialogBoxIndirectParam...(...)
{
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;
    delete g_dlgProcStack;
    g_dlgProcStack = procItem;
}

// A wrapper dialog procedure will allow us to capture the
// SC_CONTEXTHELP button on the title bar from Windows and
// forward it as a simple WM_HELP message back to the dialog.

INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,
    WPARAM wParam, LPARAM lParam)
{
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)
    {
        uMsg = WM_HELP;
        wParam = 0;
        lParam = 0;
    }
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,
        hwndDlg, uMsg, wParam, lParam);
}
```

##### <a name="help-buttons-in-managed-code"></a>Botones de ayuda en código administrado
 Invalidar el comportamiento predeterminado del botón Ayuda de la barra de título de la ventana es fácil en el código administrado. A continuación se muestra una aplicación de demostración completa que muestra este comportamiento. Básicamente, debe invalidar el método **WndProc** del formulario y, a continuación, desactivar las solicitudes de ayuda F1 cuando se intercepta SC_CONTEXTHELP mensaje. 

```
using System;
using System.Windows.Forms;

public class HelpForm : Form
{
    private const int SC_CONTEXTHELP = 0xF180;
    private const int WM_SYSCOMMAND = 0x0112;

    public HelpForm()
    {
        this.ClientSize = new System.Drawing.Size(300, 250);
        this.HelpButton = true;
        this.MaximizeBox = false;
        this.MinimizeBox = false;
        this.Name = "HelpForm";
        this.Text = "Help Form";
    }

    protected override void WndProc(ref Message m)
    {
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)
            ShowHelp();
        else
            base.WndProc(ref m);
    }

    private void ShowHelp()
    {
        MessageBox.Show("F1 Help goes here.");
    }

     [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.EnableRTLMirroring();
        Application.Run(new HelpForm());
    }
}
```

## <a name="see-also"></a>Consulta también
- [Fuentes y formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [Notificaciones y progreso para Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
