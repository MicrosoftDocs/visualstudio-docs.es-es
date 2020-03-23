---
title: Texto de UI y ayuda
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea4f2b49838340fcee41bc9c41ef94558e44825e
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301246"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Texto de la interfaz de usuario y ayuda para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a>Texto y terminología de la interfaz de usuario
 El texto comprensible es crucial para una interfaz de usuario eficaz. Los usuarios de software tienden a leer las etiquetas primero, a saber, las más relevantes para completar la tarea en cuestión. El texto estático se lee con menos frecuencia. Planifique que los usuarios inicien sus sesiones de trabajo con un análisis rápido de toda la ventana, seguido de una lectura de la interfaz de usuario en este orden aproximado:

1. Controles interactivos en el centro

2. Botones de confirmación

3. Controles interactivos encontrados en otros lugares

4. Principales instrucciones

5. Explicaciones suplementarias

6. Título de la ventana

7. Otro texto estático en el cuerpo principal

### <a name="usage-patterns-for-ui-text"></a>Patrones de uso para el texto de la interfaz de usuario

#### <a name="title-bar-text"></a>Texto de la barra de título
 El texto de la barra de título debe coincidir con el comando que generó la interfaz de usuario.

#### <a name="instructional-text-helper-text"></a>Texto instructivo (texto auxiliar)
 En algunos cuadros de diálogo, es útil proporcionar instrucciones principales prominentes para explicar qué hacer en la ventana o en la página. Esto se conoce a veces como "texto auxiliar".

##### <a name="writing-style-rules-for-helper-text"></a>Reglas de estilo de escritura para texto auxiliar

- No expliques lo obvio. A menos que sea absolutamente necesario, no incluya texto instructivo.

- El texto instructivo siempre se coloca en la parte superior del cuadro de diálogo y debe hacer referencia a la tarea que se está realizando.

- Explicar con precisión a los usuarios lo que tienen que hacer. Evite la comunicación excesiva y la redundancia.

- Revise cada ventana y elimine las palabras y las declaraciones duplicadas.

- Mantenga el texto instructivo corto. Si se necesita más información para determinados usuarios o escenarios, proporcione un vínculo a un tema conceptual en línea detallado.

- Escribe tu texto para que cada palabra tenga peso y sea necesaria.

- Siga las instrucciones existentes de Microsoft para el texto y el estilo y el [tono](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx)de la interfaz de [usuario.](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)

#### <a name="supplemental-instructions"></a>Instrucciones suplementarias
 Las instrucciones complementarias proporcionan información adicional que ayuda al usuario a comprender los controles o las agrupaciones de control. Esto también podría incluir el texto de sugerencia necesario para comprender qué formato espera el control de entrada. Utilice instrucciones suplementarias con moderación. Reservarlos para los casos en los que es probable que el usuario no comprenderá completamente las ramificaciones de la elección que están haciendo.

 ![Texto complementario en Visual Studio](../../extensibility/ux-guidelines/media/0601-b-supplementaltext1.png "0601-b_SupplementalText1")

 **Texto complementario en Visual Studio**

 ![Texto complementario en Visual Studio](../../extensibility/ux-guidelines/media/0601-c-supplementaltext2.png "0601-c_SupplementalText2")

 **Texto complementario en Visual Studio**

#### <a name="infotips"></a>Consejos de información
 A menudo, el texto instructivo puede ser demasiado largo para colocar en el lugar en la interfaz de usuario o puede ser útil sólo para los nuevos usuarios, sintiéndose como desorden para los usuarios experimentados. En este caso, el texto instructivo/informativo debe colocarse como información sobre herramientas en una información sobre información.

 Las sugerencias de información deben colocarse cerca de los controles con los que están relacionados y deben usar el icono de información específica, que es discreto pero perceptible.

 ![Panel informativo en Visual Studio](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601-d_InfoTip")

 **Ejemplo de información en Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Reglas de estilo de escritura para InfoTips

- Escriba InfoTips como oraciones completas. Requieren verbos específicos, mayúsculas y minúsculas y puntuación final.

- Utilice InfoTips para complementar su instrucción o información principal. Si solo estás usando palabras diferentes para volver a decir la idea principal, no necesitas una información.

- Mantenga InfoTips cortos y dulces. Utilice palabras pequeñas y un lenguaje sencillo y cotidiano que apoye y anime al usuario.

- Siga las instrucciones existentes de Microsoft para el texto y el estilo y el [tono](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx)de la interfaz de [usuario.](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)

#### <a name="control-labels"></a>Etiquetas de control
 Las etiquetas de control deben ser cortas, concisas y seguir las instrucciones de escritorio de [Windows para controles](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx).

 Para obtener más información sobre el formato de etiqueta de control y la ubicación dentro de la interfaz de usuario, consulte [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Vínculos a la Ayuda
 Los vínculos de ayuda se pueden colocar en el texto de instrucción o en el cuerpo de la interfaz de usuario. Pueden ser vínculos a Ayuda o iniciar diálogos internos.

##### <a name="visual-style-rules-for-help-links"></a>Reglas de estilo visual para vínculos de ayuda

- Utilice los colores de entorno correctos para los hipervínculos. Un hipervínculo con el estilo correcto no parpadeará brevemente en rojo cuando se haga clic en él. Si ve esto, entonces es una indicación de que los colores del entorno no se están utilizando.

- Los subrayados solo se deben usar al mantener el mouse o cuando el vínculo está incrustado en un párrafo.

- Para obtener información más detallada sobre los estilos visuales y de interacción de hipervínculos, consulte Botones e hipervínculos.

##### <a name="writing-style-rules-for-help-links"></a>Reglas de estilo de escritura para vínculos de ayuda

- Al iniciar cuadros de diálogo, mantenga los estándares para los puntos suspensivos: no hay puntos suspensivos para la navegación, puntos suspensivos si la tarea requiere interfaz de usuario adicional.

     ![Vínculo de ayuda en Visual Studio](../../extensibility/ux-guidelines/media/0601-e-helplink.png "0601-e_HelpLink")

     **Los puntos suspensivos (...) en un vínculo de Ayuda indican que la tarea requerirá una interfaz de usuario adicional.**

- Los vínculos no deben comenzar con "Aprender", ya que esa no es la intención del usuario. El usuario quiere responder a una pregunta específica, no recibir una educación general.

- Enlaces de ayuda de frase para que hagan la pregunta que el tema responderá.

     Error: "Más información sobre los precios de Windows Azure Mobile Services"

     Correcto: "¿Qué opciones de precios están disponibles para Windows Azure Mobile Services?"

- Nunca use *Click...* al texto del enlace.

- Nunca vincules sólo la palabra "aquí". Esto es problemático para algunos lectores de pantalla, que solo expresarán la palabra hiperenlace.

     Error: "Buscar información en Windows Azure Mobile Services **aquí"**

     Correcto: "¿Qué opciones de precios están disponibles para Windows Azure Mobile Services?"

- Para obtener más información sobre el estilo de escritura correcto para los vínculos de Ayuda, consulte las instrucciones de Escritorio de [Windows para Obtener ayuda](https://msdn.microsoft.com/library/windows/desktop/dn742494\(v=vs.85\).aspx).

#### <a name="hint-text"></a>Texto de sugerencia
 El texto de sugerencia aparece como una marca de agua dentro de un control o debajo del control. El formato correcto se aplicará mediante el `Environment.GrayText`token VSColors adecuado, .

 Puede aparecer en una serie de formas.

- En lugar de la etiqueta de control:

     ![Texto de sugerencia en Visual Studio](../../extensibility/ux-guidelines/media/0601-f-hinttext1.png "0601-f_HintText1")

- Con un verbo, dando instrucciones:

     ![Texto de sugerencia en Visual Studio](../../extensibility/ux-guidelines/media/0601-g-hinttext2.png "0601-g_HintText2")

- Con texto que indica una entrada obligatoria:

     ![Texto de sugerencia en Visual Studio](../../extensibility/ux-guidelines/media/0601-h-hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Texto de marca de agua
 En una superficie de diseño vacía, el texto debe indicar qué hacer, así como proporcionar vínculos para abrir otras ventanas relacionadas, si procede:

 ![Texto de marca de agua en Visual Studio](../../extensibility/ux-guidelines/media/0601-i-watermarktext.png "0601-i_WatermarkText")

 **Ejemplo de texto de marca de agua en Visual Studio**

### <a name="common-terminology"></a>Terminología común

|Término|Explicación|Comentario|
|----------|-----------------|-------------|
|Iniciar sesión / Cerrar sesión|Verbos utilizados como sinónimos de la web para representar la autenticación en una propiedad web. Dentro de los clientes, usamos esta única vez como una noción de nivel superior para iniciar y cerrar sesión en la conexión de usuario IDE, que representa una identidad de nivel superior que proporciona capacidades de nivel superior, como itinerancia y licencias que no están disponibles con todas las demás conexiones.|El usuario IDE es la única característica que debe representar un verbo de inicio /cierre de sesión, ya que representa el usuario IDE de nivel superior.|
|Conectar / Desconectar|Utilícelo en lugares donde una característica mantiene una sola conexión a un servicio en línea.|El Explorador de servidores, donde solo puede tener una conexión de Azure activa a la vez, es un ejemplo de Conectar/Desconectar.|
|Añadir / Eliminar|No destructivo. Utilícelo al agregar o quitar algo de una lista.|El cuadro de diálogo de lista de servidores de TFS Connection Manager es un ejemplo de Agregar o quitar.|
|Eliminar|Destructivo. Utilícelo solo cuando el elemento que se va a quitar se descarte o elimine permanentemente del disco.|"Eliminar" generalmente requiere un mensaje si el resultado es eliminar un archivo del disco.|

## <a name="error-messages"></a>Mensajes de error

### <a name="overview"></a>Información general
 Se producen errores. Establecer limitaciones en lo que el usuario puede hacer es un primer paso sensato para evitar mensajes de error evitables. Sin embargo, cuando se produce un error, un mensaje de error bien escrito puede ir un largo camino hacia la mitigación del problema. Los mensajes de error son posiblemente uno de los tipos más importantes de notificación que el usuario ve, porque son sincrónicos e indican un problema que debe resolverse. Los mensajes de error mal escritos dejan a los usuarios por su cuenta para decidir la causa de los errores y cualquier posible solución.

 Los usuarios pueden dejar de prestar atención a los mensajes de error sobreutilizados o confusos, por lo que escribir sólo los mensajes necesarios que agregan valor a la experiencia del usuario. Si el mensaje es simplemente una notificación, utilice una presentación alternativa.

### <a name="rules-for-creating-an-error-message"></a>Reglas para crear un mensaje de error

- Al construir mensajes de error, elija el nivel de error adecuado para la audiencia. Apunte a resúmenes sencillos que proporcionen una acción que el usuario pueda realizar, si corresponde. No indique nada que el usuario no necesite saber.

- Proporcionar asistencia constructiva. Es más fácil leer y actuar en un mensaje de error que contiene instrucciones.

- No uses dobles negativos.

- Realice una comprobación automática y manual de gramática y ortografía en cualquier mensaje de error que escriba.

- Para mensajes de error complejos, evite las comunicaciones secuenciales. Nunca utilice una conexión F1 para el mensaje de error. El mensaje en sí debe ser suficiente.

- Utilice el icono correcto.

- Haga que las preguntas sean fáciles de entender y use botones que tengan opciones claras, como "Eliminar" y "Cancelar".

- En el caso de las advertencias, tenga claro cuál será la consecuencia del procedimiento. Los botones deben indicar la consecuencia.

- En caso de errores, describa lo que el usuario puede hacer para solucionar el problema. Los botones deben ser acciones o decir "Cerrar". No utilice un botón "OK" para un mensaje de error.

- Algunas preguntas que debe hacerse al construir un mensaje de error:

  - ¿Puede el usuario averiguar cómo resolver el problema con este error solo?

  - ¿Utiliza el usuario el mismo vocabulario que este error?

  - ¿Este error es ambiguo o compartido en varias situaciones? Si es así, ¿cómo guía a los usuarios a la solución que necesitan?

#### <a name="build-errors"></a>Errores de compilación
 Dado que Visual Studio es una herramienta de desarrollo de software, muchos de sus componentes tienen un paso de compilación, conversión o codificación para convertir el trabajo del desarrollador a formato binario. Estas conversiones pueden provocar errores cuando el compilador no puede procesar archivos creados incorrectamente o cuando las opciones del compilador no se establecieron correctamente.

 Los usuarios de Visual Studio pueden pasar un gran número de horas de desarrollo resolviendo errores de compilación. Este tiempo de resolución aumenta cuando los errores tienen dependencias o cuando los mensajes de error están mal escritos, lo que puede dificultar la detección del origen del error.

 Los mejores errores de compilación son los que no se producen en primer lugar, por lo que Visual Studio proporciona Autocompletar e IntelliSense ondea. Los validadores de esquema y herramientas similares proporcionan el mismo tipo de comentarios. Estos mecanismos guían proactivamente al usuario para construir código bien formado, lo que disminuye la posibilidad de errores de compilación.

 Visual Studio proporciona una ventana de herramientas donde los usuarios pueden leer y navegar a través de los errores que se produjeron en sus ventanas de documento. Se proporcionan métodos abreviados de teclado para que el usuario pueda navegar rápidamente por grandes cantidades de código e ir directamente a la ubicación del problema. Visual Studio también permite que cada error de compilación se ata a un identificador de contexto o palabra clave de Ayuda determinado para que el usuario pueda ir directamente a un tema de Ayuda que proporciona información más detallada sobre el error.

 Escriba errores de compilación claros y concisos:

- **Utilice un lenguaje sencillo** que explique el problema con poca o ninguna jerga del compilador. El texto de un error de compilación no debe ser demasiado técnico.

- **Esbozar posibles causas.** Por ejemplo, "Falta un signo de dos puntos entre la propiedad y el valor en la declaración '(property) : (value)'."

- Proporcione detalles sobre posibles correcciones. Si no hay suficiente espacio, se pueden poner detalles adicionales en el tema de Ayuda correspondiente.

### <a name="components-of-a-well-written-error-message"></a>Componentes de un mensaje de error bien escrito

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Utilice el servicio de diálogo de shell para los mensajes de error.
 El uso del servicio de diálogo de shell le permite controlar el aspecto del mensaje (en particular las fuentes) sin cambios importantes en elementos individuales. Use los mecanismos **IErrorInfo** e infórmelos mediante **IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Elija una presentación de notificación eficaz y adecuada.
 Utilice un cuadro de diálogo modal con una advertencia crítica si se requiere una acción inmediata para evitar la pérdida de datos (notificación sincrónica). Los iconos críticos están reservados para situaciones en las que cerrar el mensaje sin leerlo puede dar lugar a consecuencias negativas. La pérdida de datos es una situación crítica que requiere una respuesta a nivel de alarma. El uso excesivo del icono crítico desensibiliza a los usuarios a su importancia. Si el mensaje de error es de naturaleza informativa, considere alternativas a un cuadro de diálogo modal (notificación asincrónica).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Proporcione una explicación limpia y sucinta de por qué ocurrió el problema en lugar de una explicación técnica.
 Sobrecargar a los usuarios con detalles técnicos en la explicación hará que sean más propensos a ignorar los mensajes de error. Ejemplos de buenos mensajes:

- "No se puede abrir el archivo solicitado."

- "No se puede conectar a Internet."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Proporcione información sobre cómo solucionar el problema.
 Ofrezca al usuario sugerencias de cómo solucionar el problema. Sea honesto con el usuario si no hay sugerencias. Proporcionar enlaces directos a fuentes alternativas en línea, como soporte técnico o soporte de la comunidad. Intente apuntar a los usuarios a información específica en línea pertinente al problema. Para un identificador de error, considere la posibilidad de vincular a los usuarios a un subproceso de discusión sobre ese error específico. Ejemplos de buenos mensajes:

- "Asegúrese de que está conectado a Internet e intente esta operación de nuevo."

- "Asegúrese de que el archivo existe y que tiene permiso para abrirlo."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Escriba un mensaje que sea corto y al grano.
 Un mensaje de error puede notificar, explicar y ofrecer una solución, pero aún así se omite si es demasiado wordy. Una solución es usar la divulgación progresiva con un botón de detalles. Por ejemplo, proporcione una breve descripción/solución y, a continuación, coloque más detalles en un botón de detalles. Si los usuarios eligen leer más información sobre el error, pueden hacerlo.

 El idioma del mensaje debe ser:

- **Apropiado para el dominio.** Utilice el idioma que el usuario entenderá. A pesar de que nuestros clientes son desarrolladores, a menudo no tienen el contexto y la terminología que tenemos.

- **Específico.** Evite la redacción vaga y dé nombres y ubicaciones específicos de los objetos involucrados. Por ejemplo, un mensaje de error como "carácter no es válido" no es útil. ¿Qué personaje? "Archivo no encontrado." ¿Qué archivo?

- **Cortés.** No culpes al usuario ni lo hagas sentir estúpido. Evite el lenguaje hostil u ofensivo (matar, ejecutar, terminar, fatal, ilegal). Evite el texto en mayúsculas, que a menudo se ve como gritos y no es tan legible. No uses humor.

- **Correcto.** Utilice la ortografía y la gramática correctas (incluso en alfas). Los typos no son profesionales y embarazosos.

- **Contextualmente apropiado.** Utilice el texto del botón adecuado. Evite el botón "Aceptar" y en su lugar use "Continuar" o "Sí/No."

### <a name="error-message-examples"></a>Ejemplos de mensajes de error

|Bueno|Incorrecto|
|----------|---------|
|"El número que marcó ya no está en servicio. Compruebe el número y marque de nuevo o marque 0 para el operador."|- "Error (449): Número ilegal"<br />- "Este error de excepción no controlado indica que la operación se completó correctamente."<br /><br /> ![Mensaje de error incorrecto en Visual Studio](../../extensibility/ux-guidelines/media/0602-a-errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Obtener acceso a la Ayuda

### <a name="overview"></a>Información general
 Además de la documentación de MSDN, un usuario de Visual Studio tiene varios puntos de acceso para ayudar al usuario mientras está en la interfaz de usuario. Para garantizar que estos puntos de acceso estén disponibles de forma coherente, los equipos de entidades deben aprovechar el sistema de ayuda que ofrece el entorno. Estos puntos de acceso son:

- **Texto instructivo y suplementario en diálogos.** Texto estático que proporciona dirección o explicación, ya sea en la superficie de la interfaz de usuario o disponible al pasar el cursor sobre un icono de información.

- **Ayuda de F1** (solo editor). En el editor de Visual Studio, un usuario puede confiar en que, en cualquier momento, al presionar F1 aparecerá un tema de Ayuda específico para la selección actual. Asegúrese de que los temas asociados con F1 sean adecuados e informativos.

- **Hipervínculos a temas de ayuda.** Un hipervínculo dentro de un cuadro de diálogo, una ventana de herramientas o una superficie de diseño que inicia un tema para ayudar al usuario a obtener más información sobre una tecnología, capacidad o información sobre cómo realizar una tarea.

- **Mecanismos de interfaz de usuario auxiliares, como etiquetas inteligentes y cuadros de diálogo de creación.** Estos mecanismos ayudan al usuario a comprender un elemento de interfaz de usuario o facilitan una tarea, como etiquetas inteligentes o cuadros de diálogo del generador.

- **Botones** de ayuda de la interfaz de usuario (obsoleto). Un indicador visible en la barra de título que da acceso al tema de Ayuda de F1 relacionado.

### <a name="text"></a>Texto

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Texto instructivo y suplementario en diálogos
 En los cuadros de diálogo que admiten tareas complejas, puede ser necesario proporcionar texto instructivo dentro de la interfaz de usuario, a menudo en la parte superior del cuadro de diálogo o cerca de controles complejos. Consulte texto y terminología de la [interfaz](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) de usuario para obtener más información sobre el estilo de escritura.

#### <a name="infotips"></a>Consejos de información
 A menudo, el texto instructivo puede ser demasiado largo para colocar en su lugar en la interfaz de usuario o puede ser útil sólo para los nuevos usuarios, sintiéndose como desorden para los usuarios experimentados. En este caso, el texto instructivo/informativo debe colocarse como información sobre herramientas en una información sobre información.

 Las sugerencias de información deben colocarse cerca de los controles con los que están relacionados y deben usar el icono de información específica, que es discreto pero perceptible.

 ![Panel informativo en Visual Studio](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601-d_InfoTip")

 **Ejemplo de información en Visual Studio**

### <a name="interactive-help-mechanisms"></a>Mecanismos de ayuda interactiva

#### <a name="f1-help"></a>Ayuda F1
 La Ayuda de F1 es necesaria dentro de un editor o una superficie de diseño, pero no en ningún otro lugar del entorno de Visual Studio.

#### <a name="hyperlinks-to-help-topics"></a>Hipervínculos a temas de ayuda
 Los hipervínculos se pueden usar para realizar una acción, navegar dentro del IDE o iniciar la Ayuda en un explorador. Consulte texto y terminología de la [interfaz](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) de usuario para obtener más información sobre el idioma y 07.10.01 Botones e hipervínculos para obtener instrucciones visuales y de diseño.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Botones de ayuda [?] en las barras de título del cuadro de diálogo (obsoleto)
 En su mayor parte, los botones Ayuda [?] de la barra de título de los cuadros de diálogo están en desuso. Los temas de la interfaz de usuario ya no forman parte de nuestro modelo de documento y, por lo tanto, es posible que no haya un tema relevante al que vincularse. Esencialmente, el botón de la barra de título era lo mismo que la Ayuda de F1, y eso ya no es necesario en los cuadros de diálogo. En algunos casos, esto todavía se puede utilizar como un indicador de que hay más información conceptual o de procedimiento disponible, aunque los hipervínculos se utilizan más comúnmente en la interfaz de usuario más reciente.

##### <a name="dialogs-created-through-the-environment"></a>Diálogos creados a través del entorno
 Muchos cuadros de diálogo de shell se crean a través de la función **VBDialogBoxParam.** Esta función compartida se actualizó para ayudar a mover el botón **Ayuda** desde el cuadro de diálogo al **?** conserve una arquitectura compatible con versiones anteriores y extensible.

 En concreto, la función **VBDialogBoxParam** examina la plantilla de cuadro de diálogo de un botón cuyo identificador es **IDHELP** (9) o la etiqueta es **Ayuda** o **&Ayuda**. Si se encuentra un botón Ayuda, se oculta y el **estilo WS_EX_CONTEXTHELP** se agrega al cuadro de diálogo, que coloca el **?** en la barra de título del cuadro de diálogo.

 Cuando se crea el cuadro de diálogo, inserta el proceso de diálogo en una pila e invoca el cuadro de diálogo con un proceso de diálogo de preprocesamiento denominado **DialogPreProc**. Cuando el **?** se hace clic en el botón, envía una **WM_SYSCOMMAND** de **SC_CONTEXTHELP** al cuadro de diálogo. **El DialogPreProc** captura este comando y lo cambia a un mensaje **de WM_HELP,** que se pasa al proceso de diálogo original.

 La mayoría de los cuadros de diálogo creados por el entorno tienen un botón Ayuda en el cuadro de diálogo. Cuando se muestra el cuadro de diálogo, el botón Ayuda se oculta automáticamente y solo el **?** botón funciona. Si el **?** botón se elimina o cambia en Windows, esta solución le permite volver rápidamente a los botones de Ayuda originales.

 Esta solución hace cuatro suposiciones que podrían causar errores:

- El botón de ayuda del cuadro de diálogo es **IDHELP** (9).

- El cuadro de diálogo parece correcto cuando el botón Ayuda está oculto.

- El cuadro de diálogo no sustituye su winproc.

- El cuadro de diálogo no está incrustado dentro de otro cuadro de diálogo.

  Si el cuadro de diálogo reside en msenv y no usa **VBDialogBoxParam**, investigue el aprovechamiento de **VBDialogBoxParam** antes de implementar su propio controlador.

##### <a name="dialogs-created-through-other-packages"></a>Diálogos creados a través de otros paquetes
 Puede implementar su propia solución para los cuadros de diálogo que residen fuera de msenv. Para una clase de cuadro de diálogo compartido en el VSPackage, considere la posibilidad de mover el botón a la barra de título o implementar un controlador en cada cuadro de diálogo. El código siguiente es un esqueleto de una implementación para ayudarle a empezar:

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
 Reemplazar el comportamiento predeterminado del botón Ayuda de la barra de título de la ventana es fácil en el código administrado. A continuación se muestra una aplicación de demostración completa que muestra este comportamiento. En esencia, debe invalidar el método **WndProc** del formulario y, a continuación, activar las solicitudes de ayuda F1 cuando se intercepta un mensaje **de SC_CONTEXTHELP.**

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

## <a name="see-also"></a>Consulte también
 [Fuentes y formato para Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md) Layout para visual [studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md) [notifications and Progress for Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
