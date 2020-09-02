---
title: Texto y ayuda de la interfaz de usuario para Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3247aeaa702b59722471c7d28e98957f04f3e07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698296"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Texto de la interfaz de usuario y ayuda para Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a> Texto y terminología de la interfaz de usuario
 El texto comprensible es fundamental para la interfaz de usuario eficaz. Los usuarios de software suelen leer etiquetas en primer lugar, es decir, las más relevantes para completar la tarea a mano. El texto estático se lee con menos frecuencia. Planee a los usuarios que inicien sus sesiones de trabajo con un examen rápido de la ventana completa, seguido de una lectura de la interfaz de usuario en este orden aproximado:

1. Controles interactivos en el centro

2. Botones de confirmación

3. Controles interactivos que se encuentran en otro lugar

4. Instrucciones principales

5. Explicaciones complementarias

6. Título de la ventana

7. Otro texto estático en el cuerpo principal

### <a name="usage-patterns-for-ui-text"></a>Patrones de uso para el texto de la interfaz de usuario

#### <a name="title-bar-text"></a>Texto de la barra de título
 El texto de la barra de título debe coincidir con el comando que generó la interfaz de usuario.

#### <a name="instructional-text-helper-text"></a>Texto informativo (texto auxiliar)
 En algunos cuadros de diálogo, resulta útil proporcionar instrucciones principales destacadas para explicar qué hacer en la ventana de o en la página. Esto se conoce a veces como "texto auxiliar".

##### <a name="writing-style-rules-for-helper-text"></a>Escribir reglas de estilo para el texto del ayudante

- No explique el obvio. A menos que sea absolutamente necesario, no incluya texto informativo.

- El texto de instrucciones siempre se coloca en la parte superior del cuadro de diálogo y debe hacer referencia a la tarea que se está llevando a cabo.

- Explique exactamente a los usuarios lo que necesitan hacer. Evite la comunicación y redundancia excesivas.

- Revise cada ventana y elimine las instrucciones y las palabras duplicadas.

- Mantenga el texto informativo breve. Si es necesario más información para determinados usuarios o escenarios, proporcione un vínculo a un tema detallado conceptual en línea.

- Escriba el texto de modo que cada palabra tenga peso y sea necesario.

- Siga las instrucciones de Microsoft existentes para el texto y el [estilo y el tono](/windows/desktop/uxguide/text-style-tone)de la [interfaz de usuario](/windows/desktop/uxguide/text-ui) .

#### <a name="supplemental-instructions"></a>Instrucciones complementarias
 Las instrucciones complementarias proporcionan información adicional que ayuda al usuario a comprender los controles o las agrupaciones de control. También podría incluir el texto de la sugerencia necesario para comprender qué formato espera el control de entrada. Use instrucciones complementarias con moderación. Reservarlas para los casos en los que es probable que el usuario no comprenda completamente las ramificaciones de la elección que están realizando.

 ![Texto complementario en Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Texto complementario en Visual Studio**

 ![Texto complementario en Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Texto complementario en Visual Studio**

#### <a name="infotips"></a>Recuadros informativos
 A menudo, el texto informativo podría ser demasiado largo para colocarlo en la interfaz de usuario o puede ser útil solo para los nuevos usuarios, sentirse como desorden para los usuarios experimentados. En este caso, el texto informativo o informativo debe colocarse como una información sobre herramientas en una sugerencia.

 Recuadros informativos se deben colocar cerca de los controles con los que están relacionados y deben usar el icono de recuadro informativo específico, que es discreto pero perceptible.

 ![Panel informativo en Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Ejemplo de un recuadro informativo en Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Escribir reglas de estilo para recuadros informativos

- Escriba recuadros informativos como frases completas. Requieren verbos específicos, mayúsculas y minúsculas, y puntuación final.

- Use recuadros informativos para complementar la instrucción o la información principal. Si solo usa palabras diferentes para volver a indicar la idea principal, no necesita un recuadro informativo.

- Mantenga recuadros informativos corto y dulce. Use pequeñas palabras y el lenguaje cotidiano normal que admita y fomente al usuario.

- Siga las instrucciones de Microsoft existentes para el texto y el [estilo y el tono](/windows/desktop/uxguide/text-style-tone)de la [interfaz de usuario](/windows/desktop/uxguide/text-ui) .

#### <a name="control-labels"></a>Etiquetas de control
 Las etiquetas de control deben ser cortas, concisas y seguir las [instrucciones del escritorio de Windows para los controles](/windows/desktop/uxguide/controls).

 Para obtener más información sobre el formato y la ubicación de las etiquetas de control dentro de la interfaz de usuario, consulte [diseño de Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Vínculos a la Ayuda
 Los vínculos de ayuda pueden colocarse dentro del texto de instrucciones o en el cuerpo de la interfaz de usuario. Pueden ser vínculos a ayuda o inicio de diálogos internos.

##### <a name="visual-style-rules-for-help-links"></a>Reglas de estilo visual para vínculos de ayuda

- Use los colores de entorno correctos para los hipervínculos. Si se hace clic en un hipervínculo con estilo correcto, no se mostrará en rojo un destello breve. Si ve esto, es una indicación de que no se usan colores del entorno.

- Los subrayados solo se deben usar al mantener el mouse o cuando el vínculo se incrusta en un párrafo.

- Para obtener información más detallada sobre los estilos visuales y de interacción para los hipervínculos, vea botones e hipervínculos.

##### <a name="writing-style-rules-for-help-links"></a>Escribir reglas de estilo para vínculos de ayuda

- Al iniciar cuadros de diálogo, mantenga los estándares para los puntos suspensivos: sin puntos suspensivos para la navegación, elipses si la tarea requiere una interfaz de usuario adicional.

     ![Vínculo de ayuda en Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Un botón de puntos suspensivos (...) en un vínculo de ayuda indica que la tarea requerirá una interfaz de usuario adicional.**

- Los vínculos no deben comenzar con "Learn", ya que no se trata de la intención del usuario. El usuario desea responder a una pregunta específica, no recibir una educación general.

- Los vínculos de ayuda de la frase le permiten formular la pregunta que el tema responderá.

     Incorrecto: "más información sobre los precios de Mobile Services de Windows Azure"

     Correcto: "¿Qué opciones de precios están disponibles para Windows Azure Mobile Services?"

- No use nunca *haga clic en...* para el texto del vínculo.

- Nunca vincule solo la palabra "aquí". Esto es problemático para algunos lectores de pantalla, lo que solo le enviará la palabra de hipervínculo.

     Incorrecto: "buscar información en Windows Azure Mobile Services **aquí**"

     Correcto: "¿Qué opciones de precios están disponibles para Windows Azure Mobile Services?"

- Para obtener más información sobre el estilo de escritura correcto para los vínculos de ayuda, consulte la [Guía de escritorio de Windows para obtener ayuda](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Texto de sugerencia
 El texto de sugerencia aparece como una marca de agua dentro de un control o debajo del control. El formato correcto se aplicará mediante el token VSColors adecuado, `Environment.GrayText` .

 Puede aparecer en varias formas.

- En lugar de la etiqueta de control:

     ![Texto de sugerencia en Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Con un verbo, que proporciona instrucciones:

     ![Texto de sugerencia en Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Con texto que indica una entrada obligatoria:

     ![Texto de sugerencia en Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Texto de marca de agua
 En una superficie de diseño vacía, el texto debe indicar qué hacer y proporcionar vínculos para abrir otras ventanas relacionadas, si es necesario:

 ![Texto de marca de agua en Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Ejemplo de texto de marca de agua en Visual Studio**

### <a name="common-terminology"></a>Terminología común

|Término|Explicación|Comentario|
|----------|-----------------|-------------|
|Inicio y cierre de sesión|Verbos usados sinónimomente de web para representar la autenticación en una propiedad Web. En los clientes, usamos esto una vez como una noción de nivel superior para iniciar y cerrar la sesión de usuario de IDE, que representa una identidad de nivel superior que proporciona capacidades de nivel superior como itinerancia y licencias que no están disponibles con todas las demás conexiones.|El usuario del IDE es la única característica que debe representar un verbo de inicio y cierre de sesión, ya que representa el usuario IDE de nivel superior.|
|Conectar/desconectar|Use en lugares donde una característica mantiene una única conexión a un servicio en línea.|Explorador de servidores, donde solo puede tener una conexión activa de Azure a la vez, es un ejemplo de conexión/desconexión.|
|Agregar o quitar|No destructiva. Se usa al agregar o quitar un elemento de una lista.|El cuadro de diálogo lista de servidores del administrador de conexiones de TFS es un ejemplo de agregar o quitar.|
|Eliminar|Retroceso. Use solo cuando el elemento que se va a quitar se descartará o eliminará permanentemente del disco.|"Eliminar" normalmente requiere un mensaje si el resultado es la eliminación de un archivo del disco.|

## <a name="error-messages"></a>Mensajes de error

### <a name="overview"></a>Información general
 Se producen errores. Establecer limitaciones en lo que el usuario puede hacer es un primer paso razonable para evitar mensajes de error que se puedan evitar. Sin embargo, cuando se produce un error, un mensaje de error bien escrito puede llegar a una gran manera de mitigar el problema. Los mensajes de error son posiblemente uno de los tipos de notificación más importantes que ve el usuario, ya que son sincrónicos e indican un problema que debe resolverse. Los mensajes de error mal escritos dejan a los usuarios por su cuenta para decidir la causa de los errores y las posibles soluciones.

 Los usuarios pueden dejar de prestar atención a los mensajes de error sobreutilizados o confusos, por lo que debe escribir solo los mensajes necesarios que agreguen valor a la experiencia del usuario. Si el mensaje es simplemente una notificación, utilice una presentación alternativa.

### <a name="rules-for-creating-an-error-message"></a>Reglas para crear un mensaje de error

- Al crear mensajes de error, elija el nivel de error adecuado para la audiencia. Objetivo para resúmenes sencillos que proporcionan una acción que el usuario puede realizar, si procede. No indique nada que el usuario no necesite conocer.

- Proporcionar asistencia constructiva. Es más fácil de leer y actuar en un mensaje de error que contiene instrucciones.

- No use valores negativos dobles.

- Realice una revisión de gramática y de ortografía manual y automatizada en cualquier mensaje de error que escriba.

- En el caso de los mensajes de error complejos, evite las comunicaciones secuenciales. Nunca use un enlace F1 para el mensaje de error. El propio mensaje debe ser suficiente.

- Use el icono correcto.

- Facilite la comprensión de las preguntas y use botones que tengan opciones claras, como "eliminar" y "Cancelar".

- En el caso de las advertencias, tenga claro cuál será la consecuencia del procedimiento. Los botones deben indicar la consecuencia.

- En el caso de los errores, describa lo que el usuario puede hacer para corregir el problema. Los botones deben ser acciones o decir "cerrar". No use un botón "Aceptar" para un mensaje de error.

- Algunas preguntas que se deben formular al crear un mensaje de error:

  - ¿El usuario puede averiguar cómo resolver el problema solo en este error?

  - ¿El usuario usa el mismo vocabulario que este error?

  - ¿Este error se ambigua o se comparte en varias situaciones? Si es así, ¿cómo guiará a los usuarios a la solución que necesitan?

#### <a name="build-errors"></a>Errores de compilación
 Dado que Visual Studio es una herramienta de desarrollo de software, muchos de sus componentes tienen un paso de compilación, conversión o codificación para convertir el trabajo del Desarrollador en formato binario. Estas conversiones pueden producir errores cuando el compilador no puede procesar archivos creados incorrectamente o cuando las opciones del compilador no se establecieron correctamente.

 Los usuarios de Visual Studio pueden dedicar un número enorme de horas de desarrollo a la resolución de errores de compilación. Este tiempo de resolución aumenta cuando los errores tienen dependencias o cuando los mensajes de error se escriben mal, lo que puede dificultar la detección del origen del error.

 Los mejores errores de compilación son los que no se producen en primer lugar, que es el motivo por el que Visual Studio proporciona líneas de subcompleta e IntelliSense en zigzag. Los validadores de esquema y las herramientas similares proporcionan el mismo tipo de comentarios. Estos mecanismos guían proactivamente al usuario para crear código correcto, lo que reduce la posibilidad de que se produzcan errores de compilación.

 Visual Studio proporciona una ventana de herramientas en la que los usuarios pueden leer los errores que se produjeron en las ventanas de documento y navegar por ellos. Se proporcionan métodos abreviados de teclado para que el usuario pueda desplazarse rápidamente por grandes cantidades de código e ir directamente a la ubicación del problema. Visual Studio también permite asociar cada error de compilación con una palabra clave de ayuda o un identificador de contexto determinados para que el usuario pueda ir directamente a un tema de ayuda que proporcione información más detallada sobre el error.

 Escriba errores de compilación claros y concisos:

- **Use el lenguaje sin formato** que explica el problema con poca o ninguna jerga del compilador. El texto de un error de compilación no debe ser demasiado técnico.

- **Describir posibles causas.** Por ejemplo, "falta un signo de dos puntos entre la propiedad y el valor en la declaración" (propiedad): (valor) ".

- Proporcione detalles sobre las posibles correcciones. Si no hay espacio suficiente, se pueden incluir detalles adicionales en el tema de ayuda correspondiente.

### <a name="components-of-a-well-written-error-message"></a>Componentes de un mensaje de error bien escrito

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Use el servicio de diálogo Shell para los mensajes de error.
 El uso del servicio de diálogo Shell le permite controlar el aspecto del mensaje, fuentes en particular, sin cambios importantes en los elementos individuales. Use los mecanismos **IErrorInfo** y notifique mediante **IVsUIShell:: SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Elija una presentación de notificación efectiva y adecuada.
 Use un cuadro de diálogo modal con una advertencia crítica si se requiere una acción inmediata para evitar la pérdida de datos (notificación sincrónica). Los iconos críticos se reservan para las situaciones en las que el cierre del mensaje sin leerlo puede provocar consecuencias negativas. La pérdida de datos es una situación crítica que requiere una respuesta de nivel de alarma. El uso excesivo del icono crítico desensitizes a los usuarios a su importancia. Si el mensaje de error es informativo por naturaleza, considere alternativas a un cuadro de diálogo modal (notificación asincrónica).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Proporcione una explicación clara y concisa de por qué se produjo el problema en lugar de una explicación técnica.
 La sobrecarga de los usuarios con detalles técnicos en la explicación hará que sea más probable que omitan los mensajes de error. Ejemplos de mensajería correcta:

- "No se puede abrir el archivo solicitado".

- "No se puede conectar a Internet".

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Proporcione información acerca de cómo corregir el problema.
 Ofrezca las sugerencias de usuario sobre cómo corregir el problema. Sea honesto con el usuario si no hay ninguna sugerencia. Proporcionar vínculos directos a orígenes en línea alternativos, como soporte técnico o soporte técnico de la comunidad. Intente apuntar a los usuarios a información en línea específica relacionada con el problema. Para un identificador de error, considere la posibilidad de vincular a los usuarios a un subproceso de discusión sobre ese error específico. Ejemplos de mensajería correcta:

- "Asegúrese de que está conectado a Internet y vuelva a intentar esta operación".

- "Asegúrese de que el archivo existe y de que tiene permiso para abrirlo".

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Escriba un mensaje corto y en el punto.
 Un mensaje de error puede notificar, explicar y ofrecer una solución, pero se puede omitir si es demasiado. Una solución es usar la divulgación progresiva con un botón detalles. Por ejemplo, proporcione una breve descripción o solución y, a continuación, coloque más detalles en un botón detalles. Si los usuarios deciden leer más información sobre el error, pueden hacerlo.

 El idioma del mensaje debe ser:

- **Dominio: adecuado.** Use el lenguaje que el usuario va a entender. Aunque nuestros clientes son desarrolladores, a menudo no tienen el contexto y la terminología que tenemos.

- **Cuestión.** Evite el texto impreciso y proporcione nombres y ubicaciones específicos de los objetos implicados. Por ejemplo, un mensaje de error como "el carácter no es válido" no es útil. ¿Qué carácter? "Archivo no encontrado". ¿Qué archivo?

- **Correcto.** No dude en el usuario ni haga sentirse estúpido. Evite el lenguaje hostil u ofensivo (Kill, Execute, Terminate, fatal, no válido). Evite el texto en mayúsculas, que a menudo se considera Shouting y no es tan legible. No use humor.

- **Correcto.** Use la ortografía y la gramática correctas (incluso en alfa). Los errores tipográficos son no profesionales y embarazosos.

- **Contextualmente adecuado.** Use el texto del botón adecuado. Evite el botón "Aceptar" y, en su lugar, use "Continue" o "yes/no".

### <a name="error-message-examples"></a>Ejemplos de mensajes de error

|Bueno|Incorrecto|
|----------|---------|
|"El número que marcó ya no se encuentra en servicio. Compruebe el número y vuelva a marcar o marque 0 para el operador ".|-"Error (449): número no válido"<br />-"Este error de excepción no controlada indica que la operación se completó correctamente".<br /><br /> ![Mensaje de error incorrecto en Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Obtener acceso a la Ayuda

### <a name="overview"></a>Información general
 Además de la documentación de MSDN, un usuario de Visual Studio tiene varios puntos de acceso para ayudar al usuario mientras se está en la interfaz de usuario. Para asegurarse de que estos puntos de acceso están disponibles de forma coherente, los equipos de características deben aprovechar el sistema de ayuda que ofrece el entorno. Estos puntos de acceso son:

- **Texto de instrucciones y complementos en los cuadros de diálogo.** Texto estático que proporciona la dirección o la explicación, ya sea en la superficie de la interfaz de usuario o disponible al mantener el puntero sobre un icono de recuadro informativo.

- **Ayuda F1** (solo editor). En el editor de Visual Studio, un usuario puede confiar en que, en cualquier momento, al presionar F1 se abrirá un tema de ayuda específico de la selección actual. Asegúrese de que los temas asociados con F1 son adecuados e informativos.

- **Hipervínculos a temas de ayuda.** Un hipervínculo dentro de un cuadro de diálogo, una ventana de herramientas o una superficie de diseño que inicia un tema para ayudar al usuario a obtener más información sobre la tecnología, la capacidad o la información sobre cómo realizar una tarea.

- **Mecanismos de la interfaz de usuario auxiliares, como etiquetas inteligentes y cuadros de diálogo de creación.** Estos mecanismos ayudan al usuario a entender un elemento de la interfaz de usuario o facilitan una tarea, como las etiquetas inteligentes o los cuadros de diálogo del generador.

- **Botones de ayuda** de la interfaz de usuario (desusado). Indicador visible en la barra de título que proporciona acceso al tema de ayuda F1 relacionado.

### <a name="text"></a>Texto

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Texto de instrucciones y complementos en los cuadros de diálogo
 En los cuadros de diálogo que admiten tareas complejas, puede ser necesario proporcionar texto informativo dentro de la interfaz de usuario, a menudo en la parte superior del cuadro de diálogo o en controles casi complejos. Vea [texto y terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) de la interfaz de usuario para más información sobre el estilo de escritura.

#### <a name="infotips"></a>Recuadros informativos
 A menudo, el texto informativo podría ser demasiado largo para colocarse en la interfaz de usuario o podría ser útil solo para los nuevos usuarios, como desorden para los usuarios experimentados. En este caso, el texto informativo o informativo debe colocarse como una información sobre herramientas en una sugerencia.

 Recuadros informativos se deben colocar cerca de los controles con los que están relacionados y deben usar el icono de recuadro informativo específico, que es discreto pero perceptible.

 ![Panel informativo en Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Ejemplo de un recuadro informativo en Visual Studio**

### <a name="interactive-help-mechanisms"></a>Mecanismos de ayuda interactiva

#### <a name="f1-help"></a>Ayuda F1
 La ayuda F1 es necesaria en un editor o en una superficie de diseño, pero no en otra parte del entorno de Visual Studio.

#### <a name="hyperlinks-to-help-topics"></a>Hipervínculos a temas de ayuda
 Los hipervínculos se pueden usar para realizar una acción, navegar dentro del IDE o iniciar la ayuda en un explorador. Vea [texto y terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) de la interfaz de usuario para obtener más información sobre los botones e hipervínculos de idioma y 07.10.01 para obtener instrucciones visuales y de diseño.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Ayuda [?] botones en las barras de título del cuadro de diálogo (desusado)
 En su mayor parte, los botones ayuda [?] de la barra de título de los cuadros de diálogo están desusados. Los temas de la interfaz de usuario ya no forman parte de nuestro modelo de documento y, por lo tanto, puede que no haya un tema relevante al que vincular. Esencialmente, el botón de la barra de título era lo mismo que la ayuda F1 y ya no es necesario en los cuadros de diálogo. En algunos casos, esto puede seguir utilizándose como un indicador de que hay más información conceptual o de procedimientos disponible, aunque los hipervínculos se utilizan con más frecuencia en la interfaz de usuario más reciente.

##### <a name="dialogs-created-through-the-environment"></a>Cuadros de diálogo creados a través del entorno
 Muchos cuadros de diálogo de Shell se crean a través de la función **VBDialogBoxParam** . Esta función compartida se actualizó para ayudar a mover el botón **ayuda** del cuadro de diálogo a la **?** y conserva una arquitectura que es compatible con versiones anteriores y extensible.

 En concreto, la función **VBDialogBoxParam** examina la plantilla de cuadro de diálogo para un botón cuyo identificador es **IDHELP** (9) o la etiqueta es **ayuda** o **&ayuda**. Si se encuentra un botón ayuda, se oculta y se agrega el estilo **WS_EX_CONTEXTHELP** al cuadro de diálogo, que coloca el **?** en la barra de título del cuadro de diálogo.

 Cuando se crea el cuadro de diálogo, envía el procedimiento de cuadro de diálogo a una pila e invoca el cuadro de diálogo con un procedimiento de cuadro de diálogo de preprocesamiento llamado **DialogPreProc**. ¿Cuándo **?** , se envía un **WM_SYSCOMMAND** de **SC_CONTEXTHELP** al cuadro de diálogo. **DialogPreProc** captura este comando y lo cambia a un mensaje **WM_HELP** , que se pasa al procedimiento de diálogo original.

 La mayoría de los cuadros de diálogo creados por el entorno tienen un botón ayuda en el cuadro de diálogo. Cuando se muestra el cuadro de diálogo **, el botón** ayuda se oculta automáticamente y solo el el botón funciona. Si el **?** el botón se quita o se cambia en Windows, esta solución permite retroceder rápidamente a los botones de ayuda originales.

 Esta solución hace cuatro suposiciones que podrían provocar errores:

- El botón ayuda del cuadro de diálogo es **IDHELP** (9).

- El cuadro de diálogo tiene un aspecto correcto cuando el botón ayuda está oculto.

- El cuadro de diálogo no sustituye a su que winproc.

- El cuadro de diálogo no se incrusta dentro de otro cuadro de diálogo.

  Si el cuadro de diálogo reside en msenv y no usa **VBDialogBoxParam**, investigue el uso de **VBDialogBoxParam** antes de implementar su propio controlador.

##### <a name="dialogs-created-through-other-packages"></a>Cuadros de diálogo creados a través de otros paquetes
 Puede implementar su propia solución para los cuadros de diálogo que residen fuera de msenv. En el caso de una clase de cuadro de diálogo compartida en el VSPackage, considere la posibilidad de mover el botón a la barra de título o de implementar un controlador en cada cuadro de diálogo. El código siguiente es un esqueleto de una implementación para ayudarle a comenzar:

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
 Invalidar el comportamiento predeterminado del botón ayuda de la barra de título de la ventana es fácil en el código administrado. A continuación se muestra una aplicación de demostración completa que muestra este comportamiento. En esencia, es necesario invalidar el método **WndProc** del formulario y, a continuación, activar las solicitudes de ayuda F1 cuando se intercepta un mensaje **SC_CONTEXTHELP** .

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

## <a name="see-also"></a>Vea también
- [Fuentes y formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [Notificaciones y progreso para Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
