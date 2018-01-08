---
title: Texto de la interfaz de usuario y la Ayuda de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 555fd622f5655a69ba77f3905a39635e01831c76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ui-text-and-help-for-visual-studio"></a>Texto de la interfaz de usuario y la Ayuda de Visual Studio
##  <a name="BKMK_UITextAndTerminology"></a>Texto de la interfaz de usuario y terminología  
 Texto comprensible es fundamental para la interfaz de usuario efectivo. Software que los usuarios tienden a leer las etiquetas en primer lugar, es decir, los más relevantes para completar la tarea en cuestión. Se lee el texto estático con menos frecuencia. Prepare un plan para que los usuarios inician sus sesiones de trabajo con un examen rápido de toda la ventana, seguido de una lectura de la interfaz de usuario en este orden aproximado.  
  
1.  Controles interactivos en el centro  
  
2.  Confirmar botones  
  
3.  Controles interactivos que se encuentra en otra ubicación  
  
4.  Instrucciones generales  
  
5.  Explicaciones adicionales  
  
6.  Título de ventana  
  
7.  Otro texto estático en el cuerpo principal  
  
### <a name="usage-patterns-for-ui-text"></a>Patrones de uso para el texto de la interfaz de usuario  
  
#### <a name="title-bar-text"></a>Texto de la barra de título  
 Texto de la barra de título debe coincidir con el comando que genera la interfaz de usuario.  
  
#### <a name="instructional-text-helper-text"></a>Texto informativo (texto auxiliar)  
 En algunos cuadros de diálogo, es útil proporcionar prominentes instrucciones generales para explicar qué hacer en la ventana o en la página. Esto se conoce a veces como "texto auxiliar".  
  
##### <a name="writing-style-rules-for-helper-text"></a>Escribir reglas de estilo para el texto de la aplicación auxiliar  
  
-   No se explican los obvios. A menos que sea absolutamente necesario, no incluya texto informativo.  
  
-   Texto informativo se sitúa siempre en la parte superior del cuadro de diálogo y debe hacer referencia a la tarea que esté realizando.  
  
-   Precisamente explicar a los usuarios que necesitan para hacer. Evitar la redundancia y comunicación excesivo.  
  
-   Revise cada ventana y eliminar las instrucciones y las palabras duplicadas.  
  
-   Mantenga el texto informativo breve. Si obtener más información es necesaria para determinados usuarios o escenarios, a continuación, proporcione un vínculo a un tema en línea conceptual detallado.  
  
-   Escriba el texto para que todas estas palabras contiene peso y es necesario.  
  
-   Siga las instrucciones de Microsoft existente para [texto de la interfaz de usuario](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) y [estilo y tono](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="supplemental-instructions"></a>Instrucciones adicionales  
 Instrucciones adicionales proporcionan información adicional que ayuda al usuario a comprender los controles o agrupaciones de control. También puede incluir texto de la sugerencia debe comprender qué formato está esperando el control de entrada. Utilice instrucciones adicionales con moderación. Reservar ellos para los casos donde es probable que el usuario no comprender perfectamente las consecuencias de la opción que va a realizar.  
  
 ![Texto complementario en Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "b_SupplementalText1 0601")  
  
 **Texto complementario en Visual Studio**  
  
 ![Texto complementario en Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "c_SupplementalText2 0601")  
  
 **Texto complementario en Visual Studio**  
  
#### <a name="infotips"></a>Recuadros informativos  
 A menudo, el texto informativo podría ser demasiado largo para colocar en lugar de la interfaz de usuario o puede ser útil solo a los nuevos usuarios, pero se puedan considerar desorden a los usuarios con experiencia. En este caso, el texto informativo informativo debe colocarse como una información sobre herramientas en un recuadro informativo.  
  
 Recuadros informativos deben colocarse cerca de los controles que están relacionados con y que debe usar el icono de recuadro informativo específico, que aún es discreto apreciable.  
  
 ![Recuadro informativo en Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "d_InfoTip 0601")  
  
 **Ejemplo de un recuadro informativo en Visual Studio**  
  
##### <a name="writing-style-rules-for-infotips"></a>Reglas de estilo de escritura de recuadros informativos  
  
-   Escribir recuadros informativos como frases completas. Requieren verbos específicos, en caso de oración y puntuación de cierre.  
  
-   Use recuadros informativos para complementar la instrucción principal o la información. Si simplemente está utilizando diferentes palabras para volver a formular la idea principal, no es necesario un recuadro informativo.  
  
-   Mantener recuadros informativos breve y conciso. Usar palabras pequeños y simple, lenguaje cotidiano que admite y favorece el usuario.  
  
-   Siga las instrucciones de Microsoft existente para [texto de la interfaz de usuario](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) y [estilo y tono](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="control-labels"></a>Etiquetas de control  
 Las etiquetas de control deben ser breve, conciso y siga el [instrucciones de escritorio de Windows para los controles](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Para obtener más información acerca de cómo controlar el formato de etiqueta y la ubicación dentro de la interfaz de usuario, consulte [diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="help-links"></a>Vínculos de ayuda  
 Vínculos de ayuda o bien pueden colocarse en el texto informativo o en el cuerpo de la interfaz de usuario. Pueden ser vínculos a la Ayuda o inicie los cuadros de diálogo internos.  
  
##### <a name="visual-style-rules-for-help-links"></a>Reglas de estilo visual para los vínculos de ayuda  
  
-   Usar los colores de entorno correcto para los hipervínculos. Un hipervínculo correctamente con estilo no parpadeará brevemente en rojo cuando hace clic en. Si ve esto, es un valor que indica que no se usan colores del entorno.  
  
-   Un subrayado solo debe usarse en al mantener el mouse o cuando el vínculo se incrusta en un párrafo.  
  
-   Para obtener más información sobre los estilos visuales y de interacción para los hipervínculos, consulte botones e hipervínculos.  
  
##### <a name="writing-style-rules-for-help-links"></a>Reglas de estilo de escritura para los vínculos de ayuda  
  
-   Al iniciar los cuadros de diálogo, mantener los estándares de puntos suspensivos: ningún botón de puntos suspensivos para la exploración, elipses si la tarea requiere la interfaz de usuario adicional.  
  
     ![Vínculo de ayuda en Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "e_HelpLink 0601")  
  
     **Puntos suspensivos (...) en un vínculo de ayuda se indican que la tarea requiere la interfaz de usuario adicional.**  
  
-   Vínculos no puede empezar por "Aprendizaje", ya no es la intención del usuario. El usuario desea responder a una pregunta específica, no reciben una educación general.  
  
-   Ayuda de frase vincula para que le piden a la pregunta que responderá el tema.  
  
     Correcto:  
     "Obtener más información sobre los precios de servicios móviles de Windows Azure"  
  
     Corregir:  
     "¿Qué opciones de precios están disponibles para Windows Azure Mobile Services?"  
  
-   No utilice nunca *haga clic en...*  para el texto del vínculo.  
  
-   Nunca vincule la palabra "aquí". Esto es problemático para algunos lectores de pantalla, que se voz solo la palabra hipervinculada.  
  
     Correcto:  
     "Encontrará información acerca de servicios móviles de Windows Azure **aquí**"  
  
     Corregir:  
     "¿Qué opciones de precios están disponibles para Windows Azure Mobile Services?"  
  
-   Para obtener más información sobre el estilo de escritura correctos para los vínculos de ayuda, consulte el [instrucciones de escritorio de Windows para obtener ayuda](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### <a name="hint-text"></a>Texto de sugerencia  
 Texto de la sugerencia aparece como una marca de agua dentro de un control o por debajo del control. Se aplicará el formato correcto mediante el token adecuado de VSColors, `Environment.GrayText`.  
  
 Pueden aparecer en varios formatos.  
  
-   En lugar de la etiqueta de control:  
  
     ![Sugerencia de texto en Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "f_HintText1 0601")  
  
-   Con un verbo, que proporciona instrucciones:  
  
     ![Sugerencia de texto en Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "g_HintText2 0601")  
  
-   Con el texto que indica una entrada requerida:  
  
     ![Sugerencia de texto en Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "h_HintText3 0601")  
  
#### <a name="watermark-text"></a>Texto de marca de agua  
 En una superficie de diseño vacía, el texto debe indicar qué se debe hacer, así como proporcionar vínculos para abrir otras ventanas relacionadas, si es necesario:  
  
 ![Marca de agua de texto en Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "i_WatermarkText 0601")  
  
 **Ejemplo de texto de marca de agua en Visual Studio**  
  
### <a name="common-terminology"></a>Terminología común  
  
|Término|Explicación|Comentario|  
|----------|-----------------|-------------|  
|Iniciar sesión / cerrar sesión|Verbos usados como sinónimos con Internet para representar la autenticación en una propiedad de la web. En los clientes, utilizaremos esto una vez como una noción de nivel superior para la firma de dentro y fuera de conexión de usuario IDE, que representa una identidad de nivel superior que proporciona capacidades de nivel superiores como la itinerancia y licencias que no están disponibles con todas las demás conexiones.|El usuario de IDE es la única característica que se debe representar un inicio de sesión / cerrar sesión verbo, tal y como representa el usuario IDE de nivel superior.|  
|Conectar / desconectar|Utilizar en lugares donde una característica mantiene una conexión única a un servicio en línea.|Explorador de servidores, donde solo puede tener una conexión activa de Azure a la vez, es un ejemplo de conectar o desconectar.|  
|Agregar o quitar|No destructiva. Utilice al agregar o quitar elementos de una lista.|El cuadro de diálogo de lista de servidor TFS Connection Manager es un ejemplo de agregar o quitar.|  
|Eliminar|Destructiva. Utilice esta opción solo cuando el elemento que se va a quitar se descartan permanentemente o se eliminan desde el disco.|Si el resultado está eliminando un archivo de disco, "Delete" requiere normalmente un símbolo del sistema.|  
  
## <a name="error-messages"></a>Mensajes de error  
  
### <a name="overview"></a>Información general  
 Se producirán errores. Establecer limitaciones en lo que puede hacer el usuario es un primer paso para evitar que los mensajes de error evitables significativo. Sin embargo, cuando se produce un error, un mensaje de error bien escritos puede ir mucho a mitigar el problema. Mensajes de error son sin duda uno de los tipos más importantes de notificación que ve el usuario, ya que son sincrónicas e indican un problema que debe resolverse. Mensajes de error mal escrita dejan a los usuarios en sus propios para decidir la causa de los errores y las posibles soluciones.  
  
 Los usuarios pueden dejar preste atención al sobreutilizado o confuso mensajes de error, por lo que la experiencia de escritura de los mensajes solo es necesario que agregar valor para el usuario. Si el mensaje es simplemente una notificación, a continuación, utilice una presentación alternativa.  
  
### <a name="rules-for-creating-an-error-message"></a>Reglas para crear un mensaje de error  
  
-   Al construir los mensajes de error, elija el nivel de error adecuado para la audiencia. El objetivo es sencillos resúmenes que proporcionan una acción que puede realizar el usuario, si procede. Estado de no todo lo que el usuario no necesita saber.  
  
-   Proporcionar asistencia constructivo. Es más fácil leerlos y actuar en un mensaje de error que contiene la instrucción.  
  
-   No use negativos dobles.  
  
-   Realizar ambas automáticamente y comprobación una gramática manual y la ortografía en cualquier mensaje de error que se escribe.  
  
-   Para los mensajes de error complejo, evitar las comunicaciones secuenciales. Nunca utilice un enlace de F1 para el mensaje de error. El propio mensaje debería ser suficiente.  
  
-   Utilice el icono correcto.  
  
-   Realizar preguntas fáciles de entender y usar los botones que tienen las opciones de borrar, por ejemplo, "Delete" y "Cancelar".  
  
-   Si hay advertencias, de ser claros sobre cuál será la desventaja de continuar. Los botones deberían indicar el resultado.  
  
-   Si hay errores, se describen lo que el usuario puede hacer para corregir el problema. Botones deberían acciones o diga "Cerrar". No use un botón "Aceptar" para un mensaje de error.  
  
-   Algunas preguntas para pregúntese lo siguiente al construir un mensaje de error:  
  
    -   ¿El usuario averiguar cómo resolver el problema con este error solo?  
  
    -   ¿El usuario usa el vocabulario del mismo como este error?  
  
    -   ¿Es este error ambiguo o compartir en varias situaciones? Si es así, ¿cómo guía a los usuarios a la solución que necesitan?  
  
#### <a name="build-errors"></a>Errores de compilación  
 Dado que Visual Studio es una herramienta de desarrollo de software, muchos de sus componentes tienen una compilación, convertir o codificación de paso para convertir el trabajo del desarrollador en formato binario. Estas conversiones pueden producir errores cuando el compilador no puede procesar archivos creados de forma incorrecta o cuando la opción del compilador no se han establecido correctamente.  
  
 Usuarios de Visual Studio pueden emplear un número enorme de horas de desarrollo resolver errores de compilación. Este tiempo de resolución aumenta cuando los errores tienen dependencias o cuando los mensajes de error mal escritos, lo que puede dificultar el fin de detectar el origen del error.  
  
 Los errores de compilación recomendados son aquellos que no se producen en el primer lugar, motivo por el que Visual Studio proporciona Autocompletar y líneas en zigzag IntelliSense. Controles de validación de esquema y otras herramientas similares proporcionan el mismo tipo de comentario. Estos mecanismos proactivamente guiarán al usuario para construir código correcto, lo que reduce la posibilidad de errores de compilación.  
  
 Visual Studio proporciona una ventana de herramientas que los usuarios pueden leer y navegar por los errores producidos en la ventana del documento. Métodos abreviados de teclado se proporcionan para que el usuario puede navegar por grandes cantidades de código y vaya directamente a la ubicación del problema rápidamente. Visual Studio también permite que cada error de compilación que estar ligada a un identificador de palabra clave y contexto de ayuda determinado para que el usuario puede ir directamente a un tema de ayuda que proporciona información más detallada sobre el error.  
  
 Errores de compilación clara y concisa de escritura:  
  
-   **Usar lenguaje sin formato** que explica el problema con poca o ninguna jerga de compilador. El texto de un error de compilación no debería ser excesivamente técnico.  
  
-   **Describir las causas posibles.** Por ejemplo, "faltan dos puntos entre la propiedad y valor en el ' (propiedad): (valor)' declaración."  
  
-   Proporcionan detalles sobre las posibles correcciones. Si no hay espacio suficiente, se pueden colocar detalles adicionales en el tema de ayuda correspondiente.  
  
### <a name="components-of-a-well-written-error-message"></a>Componentes de un mensaje de error bien escritos  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Usar el servicio de cuadro de diálogo de shell para mensajes de error.  
 Mediante el servicio de cuadro de diálogo de shell le permite controlar la apariencia del mensaje, las fuentes en concreto, sin realizar cambios importantes en los elementos individuales. Use la **IErrorInfo** mecanismos y registrarlos mediante **IVsUIShell::SetErrorInfo/ReportErrorInfo**.  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Elija una presentación de notificación eficaz y adecuado.  
 Utilice un cuadro de diálogo modal con una advertencia crítica si se requiere una acción inmediata para evitar la pérdida de datos (la notificación sincrónica). Iconos críticas están reservados para situaciones en que al cerrar el mensaje sin leer se pueden producir consecuencias negativas. Pérdida de datos es una situación crítica que requiera una respuesta de nivel de alarma. Uso excesivo del icono crítico desensitizes a los usuarios de su importancia. Si el mensaje de error es informativo por naturaleza, considere la posibilidad de alternativas a un cuadro de diálogo modal (notificación asincrónica).  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Proporciona una explicación limpia y concisa de por qué se produjo el problema en lugar de una explicación técnica.  
 Sobrecargar los usuarios con los detalles técnicos de la explicación hará que estén más probable pasar por alto los mensajes de error. Ejemplos de mensajería buena:  
  
-   "No se puede abrir el archivo solicitado."  
  
-   "No se puede conectar a Internet."  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>Proporciona información sobre cómo corregir el problema.  
 Ofrecen las sugerencias de usuario para resolver el problema. Ser sincero con el usuario si no hay ninguna sugerencia. Proporcionar vínculos directos a los orígenes en línea alternativos, como el soporte técnico o soporte técnico de la Comunidad. Intente dirija a los usuarios a información en línea específica pertinente para el problema. Para un identificador de error, considere la posibilidad de vincular a los usuarios a un subproceso de discusión acerca del error específico. Ejemplos de mensajería buena:  
  
-   "Asegúrese de que está conectado a Internet y vuelva a intentar esta operación de nuevo".  
  
-   "Asegúrese de que el archivo existe y que tiene permiso para abrirlo.".  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Escribir un mensaje que sea corto y hasta el punto.  
 Puede notificar un mensaje de error, explicar y ofrecen una solución, pero todavía se omite si resulta demasiado farragoso. Una solución consiste en usar divulgación progresiva con un botón de detalles. Por ejemplo, proporcionar una breve descripción/solución y, a continuación, colocar más detalles en un botón de detalles. Si los usuarios eligen leer más información sobre el error, pueden hacerlo.  
  
 El idioma en el mensaje debe ser:  
  
-   **Dominio que le corresponde.** Comprenderá utilizan el idioma del usuario. Aunque los clientes son los desarrolladores, a menudo no tienen el contexto y la terminología que tenemos.  
  
-   **Específica.** Evite la redacción imprecisa y asigne nombres específicos y ubicaciones de los objetos implicados. Por ejemplo, un mensaje de error, como "carácter no es válido" no es útil. ¿Cuál es el carácter? "Archivo no encontrado". ¿Qué archivo?  
  
-   **Cortés.** No culpar al usuario ni hacerle sentir estúpido. Evitar hostil u ofensiva language (kill, ejecutar, finalizar, grave, no válido). Evite poner texto en mayúsculas, que se considera a menudo gritar y no se puede leer como. No use humor.  
  
-   **Corregir.** Usar la gramática y la ortografía correcta (ni siquiera en alfa). Errores tipográficos son poco profesional y errores.  
  
-   **Como corresponda.** Utilice el texto del botón adecuado. Evite el botón "Aceptar" y en su lugar, utilice "Continue" o "Sí/No".  
  
### <a name="error-message-examples"></a>Ejemplos de mensajes de error  
  
|Bueno|Incorrecta|  
|----------|---------|  
|"El número marcado ya no está en servicio. Compruebe el número y vuelva a marcar o marcar 0 para el operador."|-"Error (449): número no válido"<br />-"Este error de excepción no controlada indica que la operación se completó correctamente".<br /><br /> ![Mensaje de error incorrecto en Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 a_ErrorDialog")|  
  
## <a name="accessing-help"></a>Acceso a la Ayuda  
  
### <a name="overview"></a>Información general  
 Además de la documentación en MSDN, un usuario de Visual Studio tiene varios puntos de acceso para ayudar al usuario mientras se encuentra en la interfaz de usuario. Para asegurarse de que estos puntos de acceso están disponibles de manera coherente, deben aprovechar las ventajas del sistema de ayuda que ofrece el entorno de los equipos de la característica. Estos puntos de acceso son:  
  
-   **Texto de instrucciones y adicional en los cuadros de diálogo.** Texto estático que proporciona la dirección o una explicación, ya sea en la interfaz de usuario disponible al mantener el mouse sobre un icono de recuadro informativo o expuesta.  
  
-   **Ayuda F1** (solo editor). En el editor de Visual Studio, un usuario puede confiar en que en cualquier momento, al presionar F1 se abrirá un tema de ayuda específica para la selección actual. Asegúrese de que temas asociados con F1 adecuado e informativos.  
  
-   **Hipervínculos a temas de ayuda.** Un hipervínculo dentro de un cuadro de diálogo, la ventana de herramientas o la superficie de diseño que inicia un tema para ayudar al usuario obtener más información acerca de una tecnología, la capacidad o la información acerca de cómo realizar una tarea.  
  
-   **Mecanismos de interfaz de usuario de aplicación auxiliar, como etiquetas inteligentes y cuadros de diálogo de creación.** Estos mecanismos ayudar al usuario en la descripción de un elemento de interfaz de usuario o facilitan una tarea, como las etiquetas inteligentes o los cuadros de diálogo de generador.  
  
-   **Botones de Ayuda de la interfaz de usuario** (en desuso). Un indicador visible en la barra de título que proporciona acceso al tema de Ayuda de F1 relacionado.  
  
### <a name="text"></a>Texto  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Texto de instrucciones y adicional en los cuadros de diálogo  
 En los cuadros de diálogo que permiten realizar tareas complejas, puede haber una necesidad de proporcionar texto informativo dentro de la interfaz de usuario, a menudo en la parte superior del cuadro de diálogo o cerca de controles complejos. Vea [UI texto y la terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obtener más información sobre la escritura de estilo.  
  
#### <a name="infotips"></a>Recuadros informativos  
 A menudo, el texto informativo podría ser demasiado larga para colocar en lugar de la interfaz de usuario o podría ser útil solo a los nuevos usuarios, pero se puedan considerar desorden a los usuarios con experiencia. En este caso, el texto informativo informativo debe colocarse como una información sobre herramientas en un recuadro informativo.  
  
 Recuadros informativos deben colocarse cerca de los controles que están relacionados con y que debe usar el icono de recuadro informativo específico, que aún es discreto apreciable.  
  
 ![Recuadro informativo en Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "d_InfoTip 0601")  
  
 **Ejemplo de un recuadro informativo en Visual Studio**  
  
### <a name="interactive-help-mechanisms"></a>Mecanismos de ayuda interactivos  
  
#### <a name="f1-help"></a>F1 Ayuda  
 Ayuda F1 es necesaria en un editor o la superficie de diseño, pero no en otro lugar en el entorno de Visual Studio.  
  
#### <a name="hyperlinks-to-help-topics"></a>Hipervínculos a temas de ayuda  
 Los hipervínculos se pueden utilizar para realizar una acción, navegar desde el IDE o iniciar la Ayuda en un explorador. Vea [UI texto y la terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obtener más información sobre el lenguaje y 07.10.01 botones e hipervínculos para instrucciones visuales y de diseño.  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Botones de Ayuda [?] de barras de título del cuadro de diálogo (obsoletos)  
 En su mayor parte, los botones de Ayuda [?] en la barra de título de los cuadros de diálogo están en desuso. Temas de la interfaz de usuario ya no forman parte de nuestro modelo de documento y, por lo tanto, no puede haber un tema correspondiente para vincular a. En esencia, el botón de barra de título se lo mismo que la Ayuda F1, y que ya no es necesaria en los cuadros de diálogo. En algunos casos, esto puede seguir usando como un indicador de que hay más información conceptual o de procedimiento disponibles, aunque los hipervínculos se utilizan normalmente en la interfaz de usuario más reciente.  
  
##### <a name="dialogs-created-through-the-environment"></a>Cuadros de diálogo creadas a través del entorno  
 Muchos de los cuadros de diálogo de shell se crean a través de la **VBDialogBoxParam** (función). ¿Esta función compartida se actualizó para ayudar a mover el **ayuda** botón desde el cuadro de diálogo para la **?** botón conservando una arquitectura que es con versiones anteriores compatibles y extensible.  
  
 En concreto, el **VBDialogBoxParam** función examina la plantilla de cuadro de diálogo para un botón cuyo identificador es **IDHELP** (9) o una etiqueta **ayuda** o **& Ayuda**. ¿Si se encuentra un botón de ayuda, está oculta y la **WS_EX_CONTEXTHELP** estilo se agrega al cuadro de diálogo, que coloca el **?** botón de barra de título del cuadro de diálogo.  
  
 Cuando se crea el cuadro de diálogo, inserta el procedimiento de cuadro de diálogo en una pila y se invoca el cuadro de diálogo con un procedimiento de cuadro de diálogo previa al procesamiento denominado **DialogPreProc**. ¿Cuando el **?** se hace clic en el botón, envía una **WM_SYSCOMMAND** de **SC_CONTEXTHELP** al cuadro de diálogo. El **DialogPreProc** captura este comando y lo cambia a un **WM_HELP** mensaje, que se pasa a en el procedimiento de cuadro de diálogo original.  
  
 Creado por el entorno de la mayoría de los cuadros de diálogo tienen un botón de ayuda en el cuadro de diálogo. ¿Cuando se muestra el cuadro de diálogo, el botón de ayuda está oculta automáticamente y solo el **?** botón funciona. ¿Si el **?** botón alguna vez se quitó o cambió en Windows, esta solución permite retroceder rápidamente a los botones de ayuda originales.  
  
 Esta solución hace cuatro suposiciones que pueden causar errores:  
  
-   Botón de Ayuda del cuadro de diálogo está **IDHELP** (9).  
  
-   El cuadro de diálogo es correcta cuando se oculta el botón Ayuda.  
  
-   El cuadro de diálogo no sustituya su winproc.  
  
-   El cuadro de diálogo no se incrusta dentro de otro cuadro de diálogo.  
  
 Si el cuadro de diálogo se encuentra en msenv y no usa **VBDialogBoxParam**, investigar el aprovechamiento de **VBDialogBoxParam** antes de implementar su propio controlador.  
  
##### <a name="dialogs-created-through-other-packages"></a>Cuadros de diálogo que se creó mediante otros paquetes  
 Puede implementar su propia solución para los cuadros de diálogo que residen fuera de msenv. Para una clase de cuadro de diálogo compartido en el paquete de VS, considere la posibilidad de mover el botón a la barra de título o implementar un controlador en cada cuadro de diálogo. El código siguiente es una estructura de una implementación que le ayudarán a empezar a trabajar:  
  
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
 Invalidar el comportamiento predeterminado de la ventana título ayuda del botón de barra es fácil en código administrado. A continuación se muestra una aplicación de demostración completa que muestra este comportamiento. En esencia, es necesario reemplazar el formulario **/ / WndProc** método y, a continuación, desencadenar desactivar la Ayuda de F1 cuando solicita un **SC_CONTEXTHELP** intercepta el mensaje.  
  
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
 [Las fuentes y el formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Diseño para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Notificaciones y progreso para Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)