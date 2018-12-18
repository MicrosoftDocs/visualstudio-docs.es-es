---
title: Texto de la interfaz de usuario y la Ayuda de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 52260b2cd401f8cdbd3a94704ab29db2f64fdc6d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842240"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Texto de la interfaz de usuario y la Ayuda de Visual Studio
##  <a name="BKMK_UITextAndTerminology"></a> Terminología y el texto de la interfaz de usuario  
 Texto comprensible es crucial para la interfaz de usuario efectivo. Los usuarios de software tienden a leer las etiquetas en primer lugar, es decir, los más pertinentes para completar la tarea en cuestión. Se lee texto estático con menos frecuencia. Plan para los usuarios pueden iniciar sus sesiones de trabajo con un examen rápido de la ventana completa, seguida de una lectura de la interfaz de usuario en este orden aproximado:  
  
1.  Controles interactivos en el centro  
  
2.  Confirmar botones  
  
3.  Controles interactivos que se encuentra en otro lugar  
  
4.  Instrucciones generales  
  
5.  Explicaciones adicionales  
  
6.  Título de ventana  
  
7.  Otro texto estático en el cuerpo principal  
  
### <a name="usage-patterns-for-ui-text"></a>Patrones de uso para el texto de la interfaz de usuario  
  
#### <a name="title-bar-text"></a>Texto de la barra de título  
 Texto de la barra de título debe coincidir con el comando que genera la interfaz de usuario.  
  
#### <a name="instructional-text-helper-text"></a>Texto informativo (texto auxiliar)  
 En algunos cuadros de diálogo, es útil proporcionar instrucciones principales destacadas para explicar qué hacer en la ventana o en la página. Esto se conoce a veces como "texto auxiliar".  
  
##### <a name="writing-style-rules-for-helper-text"></a>Escribir reglas de estilo para el texto de la aplicación auxiliar  
  
-   No se explican lo obvio. A menos que sea absolutamente necesario, no incluya texto informativo.  
  
-   Texto informativo siempre se coloca en la parte superior del cuadro de diálogo y debe hacer referencia a la tarea que realiza.  
  
-   Precisamente explicar a los usuarios lo deben hacer. Evite la redundancia y la comunicación excesivo.  
  
-   Revise cada ventana y eliminar las instrucciones y las palabras duplicadas.  
  
-   Mantenga el texto informativo en breve. Si información más es necesario para determinados usuarios o escenarios, a continuación, proporcione un vínculo a un tema en línea conceptual detallado.  
  
-   Escriba el texto para que contiene el peso de cada palabra y es necesario.  
  
-   Siga las instrucciones de Microsoft existente para [texto de la interfaz de usuario](/windows/desktop/uxguide/text-ui) y [estilo y tono](/windows/desktop/uxguide/text-style-tone).  
  
#### <a name="supplemental-instructions"></a>Instrucciones adicionales  
 Instrucciones adicionales proporcionan información adicional que ayuda al usuario a comprender los controles o las agrupaciones de control. Esto puede incluir también necesarios para comprender qué formato está esperando el control de entrada de texto de sugerencia. Use instrucciones complementarias con moderación. Reservarlos para casos donde es probable que el usuario no comprender completamente las consecuencias de la elección que están haciendo.  
  
 ![Texto complementario en Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601 b_SupplementalText1")  
  
 **Texto complementario en Visual Studio**  
  
 ![Texto complementario en Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601 c_SupplementalText2")  
  
 **Texto complementario en Visual Studio**  
  
#### <a name="infotips"></a>Recuadros informativos  
 A menudo, el texto informativo podría ser demasiado largo para colocar en el lugar en la interfaz de usuario o puede ser útil para los nuevos usuarios, ¿se siente como confusión a los usuarios experimentados. En este caso, el texto informativo informativo debe colocarse como una información sobre herramientas en un recuadro informativo.  
  
 Recuadros informativos deben colocarse cerca de los controles que están relacionados con y debe utilizar el icono de recuadro informativo específico, que aún es discreto apreciable.  
  
 ![Recuadro informativo en Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **Ejemplo de un recuadro informativo en Visual Studio**  
  
##### <a name="writing-style-rules-for-infotips"></a>Reglas de estilo de escritura de recuadros informativos  
  
-   Escribir recuadros informativos como oraciones completas. Requieren verbos específicos, en caso de oración y puntuación de cierre.  
  
-   Use recuadros informativos para complementar la instrucción principal o la información. Si simplemente usa palabras distintas para plantear la idea principal, no es necesario un recuadro informativo.  
  
-   Mantener recuadros informativos breve y conciso. Usar palabras cortas y sin formato, un lenguaje cotidiano que admite y favorece el usuario.  
  
-   Siga las instrucciones de Microsoft existente para [texto de la interfaz de usuario](/windows/desktop/uxguide/text-ui) y [estilo y tono](/windows/desktop/uxguide/text-style-tone).  
  
#### <a name="control-labels"></a>Etiquetas de control  
 Etiquetas de control deben ser breves y concisas y seguir el [orientación de escritorio de Windows para los controles](/windows/desktop/uxguide/controls).  
  
 Para obtener más información sobre el formato de etiqueta de control y la ubicación dentro de la interfaz de usuario, consulte [diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="help-links"></a>Vínculos de ayuda  
 Vínculos de ayuda o bien pueden colocarse en texto informativo o en el cuerpo de la interfaz de usuario. Pueden ser vínculos de ayuda o inician cuadros de diálogo internos.  
  
##### <a name="visual-style-rules-for-help-links"></a>Reglas de estilo visual para vínculos de ayuda  
  
-   Use los colores del entorno correcto de hipervínculos. Un hipervínculo con estilo correctamente no parpadeará brevemente en rojo cuando hace clic en. Si ve esto, es un valor que indica que no se usan colores del entorno.  
  
-   Solo debe usarse un subrayado en mantener el mouse o cuando el vínculo se incrusta en un párrafo.  
  
-   Para obtener información más detallada sobre los estilos visuales y de interacción de hipervínculos, consulte botones e hipervínculos.  
  
##### <a name="writing-style-rules-for-help-links"></a>Escribir reglas de estilo para los vínculos de ayuda  
  
-   Al iniciar los cuadros de diálogo, mantener los estándares para el botón de puntos suspensivos: ningún botón de puntos suspensivos para la navegación, elipses, si la tarea requiere la interfaz de usuario adicional.  
  
     ![Vínculo de ayuda en Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601 e_HelpLink")  
  
     **Puntos suspensivos (...) en un vínculo de ayuda se indican que la tarea requiere la interfaz de usuario adicional.**  
  
-   Vínculos no deben empezar con "Conocer", ya que no es la intención del usuario. El usuario desea responder una pregunta específica, no reciben una educación general.  
  
-   Ayuda de frase vincula para que hace la pregunta que responderá el tema.  
  
     Incorrecto:  
     "Obtener más información sobre los precios de Microsoft Azure Mobile Services"  
  
     Corregir:  
     "¿Qué opciones de precios están disponibles para Windows Azure Mobile Services?"  
  
-   No use nunca *haga clic en...*  para el texto del vínculo.  
  
-   Nunca vincule la palabra "aquí". Esto es problemático para algunos lectores de pantalla, que se solo la palabra con hipervínculo de voz.  
  
     Incorrecto:  
     "Obtenga información sobre Windows Azure Mobile Services **aquí**"  
  
     Corregir:  
     "¿Qué opciones de precios están disponibles para Windows Azure Mobile Services?"  
  
-   Para obtener más información sobre el estilo de escritura correctos para los vínculos de ayuda, consulte el [orientación de escritorio de Windows para obtener ayuda](/windows/desktop/uxguide/winenv-help).  
  
#### <a name="hint-text"></a>Texto de sugerencia  
 Texto de sugerencia aparece como una marca de agua en un control o debajo del control. Se aplicará el formato correcto con el token VSColors adecuado, `Environment.GrayText`.  
  
 Puede aparecer en varios formatos.  
  
-   En lugar de la etiqueta de control:  
  
     ![Sugerencia de texto en Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601 f_HintText1")  
  
-   Con un verbo, lo que proporciona instrucciones:  
  
     ![Sugerencia de texto en Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601 g_HintText2")  
  
-   Con el texto que indica una entrada requerida:  
  
     ![Sugerencia de texto en Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601 h_HintText3")  
  
#### <a name="watermark-text"></a>Texto de marca de agua  
 En una superficie de diseño vacía, el texto debe indicar qué hacer, así como para proporcionar vínculos para abrir otras ventanas relacionadas, si es necesario:  
  
 ![Marca de agua de texto en Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601 i_WatermarkText")  
  
 **Ejemplo de texto de marca de agua en Visual Studio**  
  
### <a name="common-terminology"></a>Terminología común  
  
|Término|Explicación|Comentario|  
|----------|-----------------|-------------|  
|Inicio de sesión / out|Verbos que se usan como sinónimos con la web para representar la autenticación en una propiedad de la web. Dentro de los clientes, usamos esta acción una vez como una noción de nivel superior para firmar dentro y fuera de conexión de usuario IDE, que representa una identidad de nivel superior que proporciona funcionalidades de nivel superior como la itinerancia y licencias que no están disponibles con todas las demás conexiones.|El usuario del IDE es la única característica que debe representar un inicio de sesión o cerrar sesión verbo, que representa el usuario del IDE de nivel superior.|  
|Conectar / desconectar|Utilizar en lugares donde una característica mantiene una conexión única a un servicio en línea.|Explorador de servidores, donde solo puede tener una conexión activa de Azure a la vez, es un ejemplo de conectar o desconectar.|  
|Agregar o quitar|No destructiva. Se utiliza cuando se agrega o quita algo de una lista.|El cuadro de diálogo Administrador de conexiones de TFS server lista es un ejemplo de agregar o quitar.|  
|Eliminar|Destructiva. Se utiliza solo cuando se quita el elemento se descartarán o se eliminan del disco permanentemente.|Si el resultado de la eliminación de un archivo de disco, "Delete" requiere normalmente un símbolo del sistema.|  
  
## <a name="error-messages"></a>Mensajes de error  
  
### <a name="overview"></a>Información general  
 Se producen errores. Establecer limitaciones en lo que puede hacer el usuario es un primer paso razonable para evitar que los mensajes de error evitables. Sin embargo, cuando se produce un error, un mensaje de error bien escrito puede ir un largo camino para mitigar el problema. Los mensajes de error son sin duda uno de los tipos más importantes de la notificación de que el usuario ve, ya que son sincrónicas e indican un problema que debe resolverse. Los mensajes de error mal escrito dejar a los usuarios en sus propias para decidir la causa de los errores y las posibles soluciones.  
  
 Los usuarios podrían dejar prestando atención a sobreutilizado o confuso mensajes de error, por lo que la experiencia de los mensajes de escritura solo es necesario que agregan valor al usuario. Si el mensaje es simplemente una notificación, a continuación, utilice una presentación alternativa.  
  
### <a name="rules-for-creating-an-error-message"></a>Reglas para crear un mensaje de error  
  
-   Al construir los mensajes de error, elija el nivel de error adecuado para el público. El objetivo es sencillo resúmenes que proporcionan una acción que puede realizar el usuario, si procede. Estado de no todo lo que el usuario no necesita saber.  
  
-   Proporcionar asistencia implícita. Es más fácil leerlos y actuar en un mensaje de error que contiene la instrucción.  
  
-   No use valores negativos del doble.  
  
-   Realizar ambos automáticamente y comprobación una ortografía y gramática manual en cualquier mensaje de error que se escribe.  
  
-   Mensajes de error complejo, evitar comunicaciones secuenciales. Nunca utilice un enlace de F1 para el mensaje de error. El propio mensaje debería ser suficiente.  
  
-   Utilice el icono correcto.  
  
-   Realice preguntas fáciles de entender y usar los botones que tienen opciones claras, por ejemplo, "Delete" y "Cancelar".  
  
-   Advertencias, de ser claro sobre cuál será la consecuencia de continuar. Los botones deben indicar el resultado.  
  
-   Si hay errores, se describe lo que el usuario puede hacer para corregir el problema. Los botones deberían acciones o diga "Cerrar". No use un botón "Aceptar" para un mensaje de error.  
  
-   Algunas preguntas que preguntarse al construir un mensaje de error:  
  
    -   ¿Puede averiguar el usuario de cómo solucionar el problema con este error por sí solo?  
  
    -   ¿El usuario utiliza el vocabulario del mismo que este error?  
  
    -   ¿Es este ambigua de error o compartidos en varias situaciones? Si es así, ¿cómo guían a los usuarios a la solución que necesitan?  
  
#### <a name="build-errors"></a>Errores de compilación  
 Dado que Visual Studio es una herramienta de desarrollo de software, muchos de sus componentes tienen una compilación, convertir o codificación de paso para convertir el trabajo del desarrollador en formato binario. Estas conversiones pueden producir errores cuando el compilador no puede procesar archivos creados de forma incorrecta o cuando las opciones del compilador no se han establecido correctamente.  
  
 Los usuarios de Visual Studio pueden dedicar una enorme cantidad de horas de desarrollo resolver errores de compilación. Este tiempo de resolución aumenta cuando los errores tienen dependencias o cuando los mensajes de error están mal escritos, lo que puede dificultar a descubrir el origen del error.  
  
 Los mejores errores de compilación son aquellos que no se producen en primer lugar, motivo por el cual Visual Studio proporciona Autocompletar y líneas en zigzag IntelliSense. Controles de validación de esquema y herramientas similares proporcionan el mismo tipo de comentarios. Estos mecanismos proactivamente guiar al usuario para construir el código tiene el formato correcto, lo que reduce la posibilidad de errores de compilación.  
  
 Visual Studio proporciona una ventana de herramientas, donde los usuarios pueden leer y navegar por los errores producidos en la ventana de documento. Se proporcionan métodos abreviados de teclado para que el usuario puede navegar por grandes cantidades de código y vaya directamente a la ubicación del problema rápidamente. Visual Studio también permite a cada error de compilación esté vinculada a un identificador de palabra clave y el contexto de ayuda determinado para que el usuario puede ir directamente a un tema de ayuda que proporciona información más detallada sobre el error.  
  
 Errores de compilación clara y concisa de escribir:  
  
-   **Usar un lenguaje claro** que explica el problema con poca o ninguna jerga de compilador. El texto de un error de compilación no debe ser demasiado técnico.  
  
-   **Describir las causas posibles.** Por ejemplo, "faltan dos puntos entre la propiedad y valor en el ' (propiedad): (valor)" declaración. "  
  
-   Proporcionar detalles acerca de posibles correcciones. Si no hay espacio suficiente, se pueden colocar detalles adicionales en el tema de ayuda correspondiente.  
  
### <a name="components-of-a-well-written-error-message"></a>Componentes de un mensaje de error bien escritos  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Usar el servicio de cuadro de diálogo de shell para mensajes de error.  
 Mediante el servicio de cuadro de diálogo de shell le permite controlar la apariencia del mensaje, las fuentes en concreto, sin cambios importantes a los elementos individuales. Use la **IErrorInfo** mecanismos y registrarlos mediante **IVsUIShell::SetErrorInfo/ReportErrorInfo**.  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Elija una presentación de notificación adecuados y eficaces.  
 Utilice un cuadro de diálogo modal con una advertencia crítica si se requiere una acción inmediata para evitar la pérdida de datos (la notificación sincrónica). Iconos críticos están reservados para las situaciones que cerrar el mensaje sin leer que puede dar lugar a consecuencias negativas. Pérdida de datos es una situación crítica que requiere una respuesta de nivel de alarma. Uso excesivo del icono crítico desensitizes a los usuarios de su importancia. Si el mensaje de error es de naturaleza informativa, considere alternativas a un cuadro de diálogo modal (notificación asincrónica).  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Proporciona una explicación sencilla y concisa de por qué se produjo el problema en lugar de una explicación técnica.  
 Los usuarios con los detalles técnicos en la explicación de sobrecargar hará que les más probable pasar por alto los mensajes de error. Ejemplos de mensajería buena:  
  
-   "No se puede abrir el archivo solicitado."  
  
-   "No se puede conectar a Internet."  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>Proporciona información sobre cómo solucionar el problema.  
 Ofrecen las sugerencias de usuario para resolver el problema. Ser honestos con el usuario si no hay sugerencias. Proporcionar vínculos directos a los orígenes en línea alternativos, como soporte técnico o soporte de la Comunidad. Intente apuntan a los usuarios a la información en línea específica pertinente para el problema. Para un identificador de error, considere la posibilidad de vinculación de usuarios a un hilo de discusión acerca del error específico. Ejemplos de mensajería buena:  
  
-   "Asegúrese de que está conectado a Internet y vuelva a intentarlo".  
  
-   "Asegúrese de que el archivo existe y que tiene permiso para abrirla".  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Escribir un mensaje que es corto y el punto.  
 Puede notificar un mensaje de error, explicar y ofrecen una solución, pero todavía se omite si resulta demasiado farragoso. Una solución consiste en usar la revelación progresiva con un botón de detalles. Por ejemplo, proporcionar una breve descripción o solución y, a continuación, poner más detalles en un botón de detalles. Si los usuarios deciden obtener más información sobre el error, pueden hacerlo.  
  
 El idioma en el mensaje debe ser:  
  
-   **Dominio adecuada.** Usar lenguaje que comprenderá el usuario. Aunque nuestros clientes son los desarrolladores, a menudo no tienen el contexto y la terminología que tenemos.  
  
-   **Específica.** Evite redacción poco precisas y asigne nombres específicos y ubicaciones de los objetos implicados. Por ejemplo, un mensaje de error, como "carácter no es válido" no es útil. ¿Cuál es el carácter? "Archivo no encontrado". ¿El archivo?  
  
-   **Correcto.** No culpar al usuario ni hacerle sentir estúpido. Evitar lenguaje ofensivo u hostil (kill, ejecutar, finalizar, grave, no válido). Evite el texto en mayúsculas, que a menudo se ve como gritar y no es tan legible. No use humor.  
  
-   **Corregir.** Utilizar correcta ortografía y gramática (incluso en alphas). Errores tipográficos son poco profesional y más comprometedores.  
  
-   **Contextualmente adecuado.** Use el texto del botón correspondiente. Evite el botón "Aceptar" y en su lugar, use "Continue" o "Yes/No".  
  
### <a name="error-message-examples"></a>Ejemplos de mensajes de error  
  
|Bueno|incorrecto|  
|----------|---------|  
|"El número que marcado ya no está en servicio. Compruebe el número y vuelva a marcar o marcar 0 para el operador."|-"Error (449): número no válido"<br />-"Este error de excepción no controlada indica que la operación se completó correctamente".<br /><br /> ![Mensaje de error incorrecto en Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 a_ErrorDialog")|  
  
## <a name="accessing-help"></a>Acceso a la Ayuda  
  
### <a name="overview"></a>Información general  
 Además de la documentación de MSDN, un usuario de Visual Studio tiene varios puntos de acceso para ayudar al usuario mientras se encuentra en la interfaz de usuario. Para asegurarse de que estos puntos de acceso están disponibles de forma coherente, deben aprovechar el sistema de ayuda que ofrece el entorno de equipos de características. Estos puntos de acceso son:  
  
-   **Texto informativo y adicional en los cuadros de diálogo.** Texto estático que proporciona la dirección o una explicación, ya sea en la interfaz de usuario disponible al mantener el mouse sobre un icono de recuadro informativo o superficial.  
  
-   **Ayuda F1** (solo editor). En el editor de Visual Studio, un usuario puede confiar en que en cualquier momento, al presionar F1 se abrirá un tema de ayuda específica para la selección actual. Asegúrese de que temas relacionados con F1 adecuado e informativos.  
  
-   **Hipervínculos a temas de ayuda.** Un hipervínculo dentro de un cuadro de diálogo, la ventana de herramientas o la superficie de diseño que se inicia un tema para ayudar al usuario obtener más información sobre una tecnología, la funcionalidad o la información sobre cómo realizar una tarea.  
  
-   **Mecanismos de interfaz de usuario auxiliar, como cuadros de diálogo de creación y etiquetas inteligentes.** Estos mecanismos ayudar al usuario en la descripción de un elemento de interfaz de usuario o facilitan una tarea, como las etiquetas inteligentes o los cuadros de diálogo del generador.  
  
-   **Botones de Ayuda de la interfaz de usuario** (en desuso). Un indicador visible en la barra de título que proporciona acceso al tema de Ayuda de F1 relacionado.  
  
### <a name="text"></a>Texto  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Texto informativo y adicional en los cuadros de diálogo  
 En los cuadros de diálogo que admiten tareas complejas, es posible que sea necesario para proporcionar texto informativo en la interfaz de usuario, a menudo en la parte superior del cuadro de diálogo o cerca de los controles complejos. Consulte [UI texto y la terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obtener más información sobre el estilo de escritura.  
  
#### <a name="infotips"></a>Recuadros informativos  
 A menudo, el texto informativo podría ser demasiado larga para colocar en lugar de la interfaz de usuario o puede ser útil para los nuevos usuarios, ¿se siente como confusión a los usuarios experimentados. En este caso, el texto informativo informativo debe colocarse como una información sobre herramientas en un recuadro informativo.  
  
 Recuadros informativos deben colocarse cerca de los controles que están relacionados con y debe utilizar el icono de recuadro informativo específico, que aún es discreto apreciable.  
  
 ![Recuadro informativo en Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **Ejemplo de un recuadro informativo en Visual Studio**  
  
### <a name="interactive-help-mechanisms"></a>Mecanismos de Ayuda interactiva  
  
#### <a name="f1-help"></a>F1 Ayuda  
 Ayuda F1 se requiere en un editor o la superficie de diseño, pero no en otro lugar en el entorno de Visual Studio.  
  
#### <a name="hyperlinks-to-help-topics"></a>Hipervínculos a temas de ayuda  
 Los hipervínculos se pueden usar para realizar una acción, navegar dentro del IDE o iniciar la Ayuda en un explorador. Consulte [UI texto y la terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obtener más información sobre el lenguaje y 07.10.01 botones e hipervínculos para ver las pautas visual y el diseño.  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Botones de Ayuda [?] de las barras de título del cuadro de diálogo (en desuso)  
 En su mayor parte, los botones de Ayuda [?] en la barra de título de los cuadros de diálogo están en desuso. Temas de la interfaz de usuario ya no forman parte de nuestro modelo de documento y, por lo tanto, no puede haber un tema pertinente para vincular a. En esencia, el botón de barra de título era lo mismo que la Ayuda F1, y que ya no es necesario en los cuadros de diálogo. En algunos casos, esto todavía sirve como un indicador de que hay más información conceptual o de procedimiento disponibles, aunque más comúnmente se usan los hipervínculos en la interfaz de usuario más reciente.  
  
##### <a name="dialogs-created-through-the-environment"></a>Diálogos creados a través del entorno  
 Muchos de los cuadros de diálogo de shell se crean a través de la **VBDialogBoxParam** función. ¿Esta función compartida se actualizó para ayudar a mover el **ayuda** botón desde el cuadro de diálogo para la **?** botón conservando una arquitectura que es con versiones anteriores compatibles y extensible.  
  
 En concreto, el **VBDialogBoxParam** función examina la plantilla de cuadro de diálogo para un botón cuyo identificador es **IDHELP** (9) o una etiqueta **ayuda** o **& Ayuda**. ¿Si se encuentra un botón de ayuda, está oculta y la **WS_EX_CONTEXTHELP** estilos se agregan al cuadro de diálogo, que coloca el **?** botón de barra de título del cuadro de diálogo.  
  
 Cuando se crea el cuadro de diálogo, inserta el procedimiento de cuadro de diálogo en una pila e invoca el cuadro de diálogo con un procedimiento de cuadro de diálogo procesamiento previo denominado **DialogPreProc**. ¿Cuando el **?** se hace clic en el botón, envía un **WM_SYSCOMMAND** de **SC_CONTEXTHELP** al cuadro de diálogo. El **DialogPreProc** captura este comando y lo cambia a un **WM_HELP** mensaje, que se pasa a en el procedimiento de cuadro de diálogo original.  
  
 Creado por el entorno de la mayoría de los cuadros de diálogo tienen un botón de ayuda en el cuadro de diálogo. ¿Cuando aparezca el cuadro de diálogo, el botón de ayuda está oculta automáticamente y solo la **?** botón funciona. ¿Si el **?** botón nunca se quita o cambia en Windows, esta solución permite volver rápidamente a los botones de ayuda originales.  
  
 Esta solución realiza cuatro suposiciones que podrían provocar errores:  
  
- Botón de Ayuda del cuadro de diálogo **IDHELP** (9).  
  
- El cuadro de diálogo parece correcta cuando se oculta el botón Ayuda.  
  
- El cuadro de diálogo no sustituya su winproc.  
  
- El cuadro de diálogo no se incrusta dentro de otro cuadro de diálogo.  
  
  Si el cuadro de diálogo se encuentra en msenv y no usa **VBDialogBoxParam**, investigar el aprovechamiento de **VBDialogBoxParam** antes de implementar su propio controlador.  
  
##### <a name="dialogs-created-through-other-packages"></a>Diálogos creados a través de otros paquetes  
 Puede implementar su propia solución para los cuadros de diálogo que residen fuera de msenv. Para una clase de cuadro de diálogo compartidos en el paquete de VS, considere la posibilidad de mover el botón a la barra de título o implementar un controlador en cada cuadro de diálogo. El código siguiente es un esqueleto de una implementación que le ayudarán a empezar a trabajar:  
  
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
 Invalidar el comportamiento predeterminado de la ventana título ayuda del botón de barra es muy sencillo en código administrado. A continuación es una aplicación de demostración completo que muestra este comportamiento. En esencia, es necesario reemplazar el formulario **WndProc** método y el fuego, a continuación, desactivar la Ayuda de F1 cuando solicita un **SC_CONTEXTHELP** intercepta el mensaje.  
  
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
 [Fuentes y formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Notificaciones y progreso para Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)