---
title: Notificaciones y progreso para Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aee6e5656142d0597ff6101da5e2e5f690f8fcc5
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863960"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Notificaciones y progreso para Visual Studio
##  <a name="BKMK_NotificationSystems"></a> Sistemas de notificación  
  
### <a name="overview"></a>Información general  
 Hay varias maneras de informar al usuario a lo que sucede en Visual Studio con respecto a sus tareas de desarrollo de software.  
  
 Al implementar algún tipo de notificación:  
  
-   **Mantener el número de notificaciones al mínimo** número efectivo. Los mensajes de notificación se deben aplicar a la mayoría de los usuarios de Visual Studio o a los usuarios de un área de característica específicos. Un uso excesivo de notificaciones puede sidetrack el usuario o disminuir percibido facilidad de uso del sistema.  
  
-   **Asegúrese de que se va a presentar mensajes claros y que requieren acción** que el usuario puede utilizar para invocar el contexto adecuado para tomar decisiones más complejos y realizar una acción posterior.  
  
-   **Presentar mensajes sincrónicos y asincrónicos adecuadamente.** Sincrónicas notificaciones indican que algo requiere atención inmediata, como cuando se bloquea un servicio web o un código de excepción. El usuario debe estar informado de esas situaciones inmediatamente de manera que requiere su aprobación, como un cuadro de diálogo modal. Notificaciones asincrónicas son las que el usuario debe conocer, pero no se precisan para actuar inmediatamente, como cuando se completa una operación de compilación o una implementación de sitios web finaliza. Esos mensajes deben ser más ambiente y sin interrumpir el flujo de tareas del usuario.  
  
-   **Use los cuadros de diálogo modales solo cuando sea necesario para evitar que el usuario realizar una acción posterior** antes de confirmar el mensaje o tomar una decisión que se presentan en el cuadro de diálogo.  
  
-   **Quitar notificaciones ambientales cuando ya no son válidos.** No es necesario descartar una notificación si ya han tomado medidas para solucionar el problema se notificó al usuario.  
  
-   **Tenga en cuenta que pueden provocar notificaciones de las correlaciones falsas.** Los usuarios pueden creer que uno o varios de sus acciones ha desencadenado una notificación cuando en realidad no hay ninguna relación causal. Ser claro en el mensaje de notificación sobre el contexto, el desencadenador y el origen de la notificación.  
  
### <a name="choosing-the-right-method"></a>Elegir el método adecuado  
 Use esta tabla para ayudarle a elegir el método adecuado para notificar al usuario del mensaje.  
  
|Método|Usar|No use|  
|------------|---------|----------------|  
|[Cuadros de diálogo de mensaje de error modal](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Se utiliza cuando se requiere una respuesta del usuario antes de continuar.|No use cuando no es necesario para impedir que el usuario e interrumpir su flujo. Evite usar los cuadros de diálogo modales si es posible mostrar el mensaje de otra manera menos intrusivo.|  
|[Barra de estado del IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Se utiliza cuando no hay información de texto ambiente sobre el estado de un proceso.|No usar en solitario. Mejor usar junto con otro mecanismo de comentarios.|  
|[Barra de información incrustada](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|En una ventana de herramientas o ventana de documento, se utiliza para notificar de progreso, estado de error, los resultados o información procesable.|No use la información no es relevante para la ubicación donde se coloca la barra de información.<br /><br /> No use fuera de una ventana de documento o herramienta.|  
|[Cursor del mouse cambia](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Puede usarse para notificar a que un proceso está ocurriendo. También se utiliza para notificar que hay un cambio de estado en el mouse, como cuando arrastrar y colocar está en curso o el cursor del mouse está en un modo determinado, como el modo de dibujo.|No realice cambios curso breve o si aleteo del cursor es probable (por ejemplo, cuando se vincula a las partes de un proceso en ejecución más larga en lugar de a todo el proceso).|  
|[Indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Usar cuando se necesita para notificar el progreso (determinado o indeterminado). Hay una variedad de tipos de indicador de progreso y de uso específicos para cada uno. Consulte [indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Ventana de Visual Studio notificaciones](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La ventana de notificaciones no es públicamente extensible. Sin embargo, sirve para comunicarse en un intervalo de mensajes acerca de Visual Studio, incluidos los problemas críticos con su licencia y notificaciones de actualizaciones a Visual Studio o a paquetes.|No utilice para otros tipos de notificaciones.|  
|[Lista de errores](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Cuando el problema se relaciona directamente con la solución actualmente abierta del usuario tiene un problema (error/advertencia/información), es posible que necesitan realizar acciones en el código.<br /><br /> Esto podría incluir, por ejemplo:<br /><br /> -Mensajes del compilador (error/advertencia/información)<br /><br /> -Los mensajes de diagnóstico y analizador código sobre el código<br /><br /> : Los mensajes de la compilación<br /><br /> Puede ser adecuado para problemas relacionados con los archivos de proyecto o solución, pero considere en primer lugar una indicación del explorador de soluciones.|No se use para los elementos que no tienen ninguna relación con el código del usuario solución abierta.|  
|Las notificaciones del Editor: bombilla|Utilícelo cuando tenga una corrección disponible para solucionar un problema que existe en el archivo abierto.<br /><br /> Tenga en cuenta que también se debe usar una bombilla para hospedar las acciones rápidas que se realizan en el código del usuario a petición, como refactorizaciones, pero en ese caso no aparecerá "style de la notificación".|No se use para los elementos que no tienen ninguna relación al archivo abierto.|  
|Las notificaciones del Editor: subrayados ondulados|Utilice esta opción para avisar al usuario a un problema con un intervalo determinado de su código abierto (por ejemplo, un subrayado ondulado rojo si hay errores).|No se use para los elementos que no hacen referencia a un intervalo determinado de su código abierto.|  
|[Barras de estado incrustada](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Utilice esta opción para proporcionar el estado relacionado con contenido o proceso en el contexto de una ventana de herramientas específica, la ventana de documento o la ventana de cuadro de diálogo.|No use para las notificaciones de producto, procesos o elementos que no tienen ninguna relación con el contenido dentro de la ventana concreta.|  
|[Notificaciones de la Bandeja de Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Usar para las notificaciones para procesos fuera de proceso de superficie o companion en las aplicaciones.|No use para las notificaciones que son relevantes para el IDE.|  
|[Burbujas de notificación](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Usar para notificar a la de un proceso remoto o cambiar **fuera** del IDE.|No se use como un medio para notificar al usuario de procesos **en** el IDE.|  
  
### <a name="notification-methods"></a>Métodos de notificación  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a> Cuadros de diálogo de mensaje de error modal  
 Un cuadro de diálogo de mensaje de error modal se utiliza para mostrar un mensaje de error que requiere acción o confirmación del usuario.  
  
 ![Mensaje de error modal](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 01_ModalErrorMessage")  
  
 **Un cuadro de diálogo de mensaje de error modal avisa al usuario de una cadena de conexión no válida a una base de datos**  
  
####  <a name="BKMK_IDEStatusBar"></a> Barra de estado del IDE  
 La probabilidad de que los usuarios de notificación de texto de la barra de estado se correlaciona con su experiencia de equipo y completo y la experiencia específica con la plataforma Windows. La base de clientes de Visual Studio tiende a ser expertos en ambas áreas, aunque los usuarios incluso con conocimientos de Windows podrían perder los cambios en la barra de estado. Por lo tanto, la barra de estado se usa mejor con fines informativos o como una indicación redundante de información había presentada en otro lugar. Cualquier tipo de información importante y que el usuario debe resolver inmediatamente debe proporcionarse en un cuadro de diálogo o en la ventana de herramienta de notificaciones.  
  
 La barra de estado de Visual Studio está diseñada para permitir varios tipos de información que se mostrará. Se divide en las regiones para comentarios, diseñador, barra de progreso, animación y cliente.  
  
 La región de comentarios y la región del diseñador siempre están visibles. La barra de progreso y la animación regiones siempre son dinámicos y se basa en el contexto de usuario. La región del diseñador tiene un ancho estático determinado por la longitud de la cadena que se extrae de un recurso para el mensaje de texto que lo acompaña. Esto permite la localización se va a ajustar el ancho sin necesidad de un cambio de código. Inglés, el ancho de esta cadena es aproximadamente 220 píxeles. La región del diseñador se comportará normalmente y la región de comentarios se absorba el espacio restante.  
  
 La barra de estado también se colorea para agregar interés visual y el valor funcional comunicación a través de varios cambios de estado IDE, como cuando el IDE está en modo de depuración.  
  
 ![Los cambios de color de la barra de estado IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 02_IDEStatusBar")  
  
 **Colores de barra de estado IDE**  
  
####  <a name="BKMK_EmbeddedInfobar"></a> Barra de información incrustada  
 Una barra de información puede usarse en la parte superior de una ventana de documento o ventana de herramientas para informar al usuario de un estado o la condición. También puede ofrecer los comandos para que el usuario puede tener una manera de actuar fácilmente. La barra de información es un control de shell estándar. Evite crear los suyos propios, que actuará y aparecen incoherente con otras personas en el IDE. Consulte [las barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) para los detalles de implementación e instrucciones de uso.  
  
 ![Incrustar barra de información](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 03_EmbeddedInfobar")  
  
 **Una barra de información incrustada en una ventana de documento, el usuario que el IDE está en modo de depuración histórica y el editor no responderá en la misma manera como lo hace en modo de depuración estándar de alertas.**  
  
####  <a name="BKMK_MouseCursorChanges"></a> Cursor del mouse cambia  
 Al cambiar el cursor del mouse, use los colores que están asociados al servicio VSColor y ya están asociadas con el cursor. Cambios de cursor pueden usarse para indicar una operación en curso, así como las zonas donde el usuario se mantiene sobre un destino que se puede arrastrar, colocado o utilizar para seleccionar un objeto de posicionamiento.  
  
 Use el cursor del mouse y la espera de disponibilidad solo cuando se debe reservar todo el tiempo de CPU disponible para una operación, impide que el usuario expresar cualquier entrada adicional. En la mayoría de los casos con aplicaciones bien escritas con multithreading, debe raras veces cuando se impide que los usuarios realizar otras operaciones.  
  
 Tenga en cuenta que los cambios del cursor son útiles, tal como presenta una indicación redundante para obtener información en otro lugar. No confíe en un cambio de cursor como la única manera de comunicarse con el usuario, especialmente cuando intenta transmitir algo que es fundamental que el usuario debe resolver.  
  
####  <a name="BKMK_NotSysProgressIndicators"></a> Indicadores de progreso  
 Indicadores de progreso son importantes para dar a los comentarios del usuario durante los procesos que tienen más de unos segundos en completarse. Se pueden mostrar indicadores de progreso en contexto (cerca del punto inicial de la acción en curso), en una barra de estado incrustada, en un cuadro de diálogo modal o en la barra de estado de Visual Studio. Siga las instrucciones de [indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) sobre su uso e implementación.  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a> Ventana de Visual Studio notificaciones  
 La ventana de notificaciones de Visual Studio notifica a los desarrolladores sobre licencias, entorno (Visual Studio), extensiones y actualizaciones. Los usuarios pueden descartar notificaciones individuales o pueden optar por omitir determinados tipos de notificaciones. La lista de notificaciones omitidas se administra en un **Herramientas > opciones** página.  
  
 La ventana de notificaciones no es extensible actualmente.  
  
 ![Ventana de Visual Studio notificaciones](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 06_VSNotificationsWindow")  
  
 **Ventana de herramientas de Visual Studio notificaciones**  
  
####  <a name="BKMK_ErrorList"></a> Lista de errores  
 Una notificación en la lista de errores se indican errores y advertencias que se produjeron durante la compilación o y proceso de compilación y permite al usuario navegar en el código para ese error concreto del código.  
  
 ![Lista de errores](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 08_ErrorList")  
  
 **Lista de errores en Visual Studio**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a> Barras de estado incrustada  
 Dado que la barra de estado IDE es dinámica, con su contexto de la región de cliente establecido en la ventana de documento activo y la información de actualización en el contexto del usuario o las respuestas del sistema, es difícil mantener una presentación continua de información o proporcionar el estado en a largo plazo procesos asincrónicos. Por ejemplo, la barra de estado IDE no es adecuada para las notificaciones de los resultados de ejecución de pruebas para varias ejecuciones o las selecciones de elementos actuar de forma inmediata. Es importante conservar dicha información de estado en el contexto de la ventana de documento o herramienta que el usuario realiza una selección o inicia un proceso.  
  
 ![Barra de estado incrustada](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 09_EmbeddedStatusBar")  
  
 **Barra de estado incrustada en Visual Studio**  
  
####  <a name="BKMK_WindowsTray"></a> Notificaciones de la Bandeja de Windows  
 El área de notificación está al lado del sistema de Windows del reloj en la barra de tareas de Windows. Muchas herramientas y componentes de software proporcionan iconos de esta área para que el usuario puede obtener un menú contextual para las tareas de todo el sistema, como cambiar la resolución de pantalla o la obtención de actualizaciones de software.  
  
 Las notificaciones de nivel de entorno se deben mostrar en el centro de notificaciones de Visual Studio, no el área de notificación de Windows.  
  
####  <a name="BKMK_NotificationBubbles"></a> Burbujas de notificación  
 Las burbujas de notificación pueden aparecer como informativo dentro de un editor o diseñador o como parte del área de notificación de Windows. El usuario percibe estos burbujas como problemas que se pueden resolver más adelante, que es una ventaja para las notificaciones no críticas. Las burbujas son apropiadas para la información importante y que el usuario debe solucionar de inmediato. Si usa las burbujas de notificación en Visual Studio, siga el [orientación de escritorio de Windows para las burbujas de notificación](/windows/desktop/uxguide/mess-notif).  
  
 ![Burbuja de notificación](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 07_NotificationBubbles")  
  
 **Burbuja de notificación en el área de notificación de Windows usada para Visual Studio**  
  
##  <a name="BKMK_ProgressIndicators"></a> Indicadores de progreso  
  
### <a name="overview"></a>Información general  
 Indicadores de progreso son una parte importante de un sistema de notificación para el envío de comentarios del usuario. Informa al usuario de finalización de procesos y operaciones. Tipos de indicadores familiar incluyen iconos animados, los cursores de giro y barras de progreso. El tipo y la ubicación de un indicador de progreso depende del contexto, incluido lo que se está informando y cuánto tiempo el proceso u operación tardará en completarse.  
  
#### <a name="factors"></a>Factores  
 Con el fin de determinar qué tipo de indicador es adecuado, deberá determinar los factores siguientes.  
  
1.  **Control de tiempo:** período de tiempo que tardará la operación  
  
2.  **Modalidad:** si la operación es modal en el entorno (bloqueos de la interfaz de usuario hasta que finalice el proceso)  
  
3.  **Persistent/transitorio:** si el resultado final del progreso debe ser visible y/o notificadas en un momento posterior  
  
4.  **Determinada o indeterminado:** si se pueden calcular la hora de finalización de la operación y el progreso  
  
5.  **Ubicación del gráfico o Textual:** si el progreso o el proceso está capturado en línea, en el cuerpo de un mensaje o un control específico, como el control de árbol  
  
6.  **Proximidad:** si debe cerca de la interfaz de usuario que está relacionado con el progreso. ¿(Por ejemplo, puede estar en la barra de estado, que puede ser muy lejos, o deben ser junto al botón que inicia el proceso)?  
  
#### <a name="determinate-progress"></a>Progreso determinada  
  
|Tipo de progreso|Cuándo y cómo usar|Notas|  
|-------------------|-------------------------|-----------|  
|Barra de progreso (determinada)|Duración de esperada > 5 segundos.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**No** insertar texto en la animación.|  
|Barra de información|Mensajería asociado a la interfaz de usuario contextual. Consulte [las barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**No** usa varias de las barras de información cuando se necesita indicar varios procesos. Use las barras de progreso apiladas en su lugar.|  
|Resultados (Ventana)|Notificación transitoria: proceso de nivel de aplicación que desea que el usuario **revisar** detalles de tras la finalización.|**No** usar si el usuario tendrá que hacer referencia a datos más adelante.|  
|Archivo de registro|Emparejado con notificación intransient en los casos, cuando es importante para **guardar** detalles después de la finalización.||  
|Barra de estado|Notificación transitoria: proceso de nivel de aplicación que el usuario hará **no necesita** detalles de tras la finalización.<br /><br /> Incluye una barra de progreso incrustado.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||  
  
#### <a name="indeterminate-progress"></a>Progreso indeterminada  
  
|Tipo de progreso|Cuándo y cómo usar|Notas|  
|-------------------|-------------------------|-----------|  
|Barra de progreso (indeterminado)|Duración de esperada > 5 segundos.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**No** insertar texto en la animación.|  
|ANTS (animados puntos horizontales)|Ida y vuelta al servidor.<br /><br /> Coloca el punto cercano de contexto entre la parte superior del contenedor primario.|**No** use si no tienen elementos primarios por contenedor todo.|  
|Spinner (anillo de progreso)|Proceso asociado a la interfaz de usuario contextual, donde el espacio es una consideración.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||  
|Barra de información|Mensajería asociado a la interfaz de usuario contextual. Consulte [las barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**No** usa varias de las barras de información cuando se necesita indicar varios procesos. Use las barras de progreso apiladas en su lugar.|  
|Resultados (Ventana)|Notificación transitoria: proceso de nivel de aplicación que el usuario deberá **revisar** detalles de tras la finalización.|**No** usar para obtener información que se debe conservar entre sesiones.|  
|Archivo de registro|Emparejado con notificación intransient en los casos, cuando es importante para **guardar** detalles después de la finalización.||  
|Barra de estado|Notificación transitoria: proceso de nivel de aplicación que el usuario hará **no necesita** detalles de tras la finalización.<br /><br /> Incluye la barra de progreso incrustado.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||  
  
### <a name="progress-indicator-types"></a>Tipos de indicador de progreso  
  
#### <a name="progress-bars"></a>Barras de progreso  
  
##### <a name="indeterminate"></a>Indeterminado  
 ![Barra de progreso indeterminada](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 04_Indeterminate")  
  
 **Barra de progreso indeterminada**  
  
 "Indeterminate" significa que todo el progreso de una operación o no se puede determinar el proceso. Utilice las barras de progreso indeterminada para las operaciones que requieren una cantidad ilimitada de tiempo o que tienen acceso a un número desconocido de objetos. Use una descripción textual para acompañar a lo que sucede. Utilizar tiempos de espera para dar a los límites a las operaciones basadas en tiempo. Barras de progreso indeterminada usar animaciones para mostrar que se está realizando progreso, pero no proporcionar ninguna otra información. No elija una barra de progreso indeterminada basándose únicamente en la falta de precisión por sí sola posibles.  
  
##### <a name="determinate"></a>Determinada  
 ![Barra de progreso determinada](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 05_Determinate")  
  
 **Barra de progreso determinada**  
  
 "Determinada" significa que una operación o un proceso requiere una cantidad limitada de tiempo, incluso si no se puede predecir con precisión ese tiempo determinado. Indicar claramente la finalización. No permita que una barra de progreso ir hasta un 100%, a menos que se ha completado la operación. Animación de la barra de progreso determinada mueve de izquierda a derecha desde 0 al 100%.  
  
 Nunca se mueva el indicador de progreso con versiones anteriores durante una operación. La barra debe avanzar constantemente cuando comience la operación y llegar a 100% cuando termina. Es el punto de la barra de progreso proporcionar al usuario una idea de cuánto tarda de toda la operación, independientemente de cuántos pasos implicados.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Simultáneas reporting (barras de progreso apiladas)  
 Si una operación tardará mucho tiempo - quizás se esté utilizando varios minutos -, a continuación, las barras de progreso de dos, uno que muestra el progreso general para una operación y otro para la progresión del paso actual. Por ejemplo, si un programa de instalación es copiar muchos archivos, puede usar una barra de progreso para indicar cuánto todo el proceso tarda mientras un segundo puede indicar qué porcentaje del archivo o directorio que se va a copiar. No se notifican más de cinco operaciones simultáneas o los procesos mediante las barras de progreso apiladas. Si tiene más de cinco operaciones simultáneas o procesos para el informe, utilice un cuadro de diálogo modal con un botón Cancelar y notificar los detalles de progreso en la ventana de salida.  
  
##### <a name="textual-descriptions"></a>Descripciones textuales  
 Use una descripción textual para acompañar a lo que sucede y el tiempo estimado para finalización. Si es imposible determinar cuánto tardará una operación, una mejor opción para enviar comentarios podría ser un icono animado en lugar de una barra de progreso.  
  
 Visual Studio proporciona una barra de progreso estándar en la barra de estado que se puede utilizar cualquier producto integrado en Visual Studio. Para obtener descripciones textuales de lo que sucede mientras la barra de progreso está animada, se puede actualizar el texto de la barra de estado.  
  
#### <a name="other-progress-indicators"></a>Otros indicadores de progreso  
  
##### <a name="ants-animated-horizontal-dots"></a>ANTS (animados puntos horizontales)  
 ![Hormigas de progreso](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 01_Ants")  
  
 "Las hormigas," animados puntos horizontales, ofrecen una referencia visual para un proceso de servidor de ida y vuelta indeterminado.  
  
##### <a name="spinner-progress-ring"></a>Spinner (anillo de progreso)  
 ![Control giratorio de progreso](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 02_Spinner")  
  
 El control de número (también conocido como un "anillo de progreso") es un indicador de progreso indeterminada que se utiliza principalmente en relación con la interfaz de usuario contextual. Mostrar un indicador giratorio en cerca de su contenido relacionado, como un encabezado de categoría textual, mensajería o control.  
  
##### <a name="cursor-feedback"></a>Comentarios del cursor  
 Para las operaciones que tienen entre 2-7 segundos, proporcionar comentarios del cursor. Normalmente, esto significa usar el cursor de espera proporcionado por el sistema operativo. Para obtener instrucciones, consulte el artículo de MSDN [Cursors.Wait propiedad](/dotnet/api/system.windows.input.cursors.wait).  
  
#### <a name="progress-indicator-locations"></a>Ubicaciones de indicador de progreso  
  
##### <a name="status-bar"></a>Barra de estado  
 La barra de estado proporciona un lugar para mostrar mensajes e información útil al usuario sin interrumpir el trabajo del usuario a la aplicación. Estado de progreso muestra normalmente en la parte inferior de una ventana, será un panel de información sobre herramientas que incluye un mensaje acerca de la medida de progreso en combinación con un indicador de la barra de progreso.  
  
 ![Barra de estado con barra de progreso](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 03_StatusBarProgressBar")  
  
 **Barra de estado con barra de progreso**  
  
 ![Barra de estado con mensajería](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 04_StatusBarMessage")  
  
 **Barra de estado con la descripción textual**  
  
##### <a name="infobar"></a>Barra de información  
 Similar a la barra de estado, la barra de información proporciona una notificación contextual y mensajería, que también se pueden emparejar con indicadores de progreso indeterminado, como la barra de progreso o el control de giro. La barra de información no debe proporcionar progreso nivel granular o indicación de progreso determinada. Consulte [las barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Barra de información con barra de progreso y la mensajería](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 05_InfoBar")  
  
 **Barra de información con barra de progreso y una descripción textual**  
  
 ![Barra de información dentro de una ventana](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 06_InfoBarInWindow")  
  
##### <a name="inline"></a>Alineado  
 Indicación del progreso en línea puede representarse mediante cualquiera de los tipos de cargador de progreso. El indicador de progreso se empareja normalmente con la mensajería, pero esto no es un requisito.  
  
 ![Control giratorio de progreso en línea](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 07_InlineSpinner")  
  
 **Combinado con la descripción textual del control de giro**  
  
 ![Barras de progreso de apiladas en línea](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 08_InlineStackedProgress")  
  
 **Barras de progreso apiladas determinada**  
  
 ![Mensajes de progreso en línea](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 09_InlineText")  
  
 **Texto insertado de Server Explorer: actualizar...**  
  
##### <a name="tool-windows"></a>Ventanas de herramientas  
 Indicación del progreso global se representa mediante una barra de progreso indeterminada situada directamente debajo de la barra de herramientas.  
  
 ![Barra de progreso indeterminada global](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 23_GlobalIndeterminate")  
  
 **Barra de progreso indeterminada global de Team Explorer**  
  
##### <a name="dialogs"></a>Cuadros de diálogo  
 Los cuadros de diálogo pueden contener cualquiera de los tipos de cargador de progreso. Indicadores de progreso pueden se empareja con mensajería así como combinar con varios niveles de indicación de progreso para representar granular y procesos de sub.  
  
 ![Cuadro de diálogo con varios tipos de indicador de progreso](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 11_Dialog")  
  
 **Cuadro de diálogo de Visual Studio con varios tipos de indicador de progreso y de procesos simultáneos**  
  
 ![Cuadro de diálogo con cargador de progreso y mensajería](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 12_Dialog2")  
  
 **Cuadro de diálogo de Visual Studio con el cargador de progreso y la mensajería de comandos en línea**  
  
##### <a name="document-well"></a>Cuadro de documento  
 El documento también puede mostrar varios tipos de cargador de progreso en combinación con los controles.  
  
 ![Mensajes de progreso en documento bien](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 13_DocumentWell")  
  
 **Barra de progreso indeterminada por debajo de la barra de herramientas**  
  
##### <a name="output-window"></a>Resultados (Ventana)  
 La ventana de salida es adecuada para controlar la progresión del proceso y el estado de progreso en curso a través de mensajería de texto insertado. Debe usar la barra de estado, junto con los informes de progreso de ventana de salida.  
  
 ![Mensajes de progreso en la ventana de salida](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 14_OutputWindow")  
  
 **Ventana de salida con el estado de proceso en curso y esperar la mensajería**  
  
##  <a name="BKMK_Infobars"></a> Barras de información  
  
### <a name="overview"></a>Información general  
 Las barras de información proporcionan al usuario un indicador cerca de su punto de atención y usar el control de barra de información compartida garantiza la coherencia en la apariencia visual y la interacción.  
  
 ![Barra de información](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904 01_Infobar")  
  
 **Barras de información en Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>El uso apropiado de una barra de información  
  
-   Para proporcionar al usuario un mensaje sin bloqueo pero importante relevante para el contexto actual  
  
-   Para indicar que la interfaz de usuario está en un determinado estado o condición que lleva a cabo algunas implicaciones de interacción, como la depuración histórica  
  
-   Para notificar al usuario que el sistema ha detectado problemas, como cuando una extensión está causando problemas de rendimiento  
  
-   Para proporcionar al usuario una manera fácil tomar las medidas, como cuando el editor detecta que un archivo ha mezclado tabulaciones y espacios  
  
##### <a name="do"></a>Hacer:  
  
-   Mantener el texto de mensaje de la barra de información cortas y en el punto.  
  
-   Mantener el texto en los vínculos y botones concisa.  
  
-   Asegúrese de que las opciones "action" que proporcionan a los usuarios son mínimas, que muestra solo las acciones necesarias.  
  
##### <a name="dont"></a>No:  
  
-   Usar una barra de información para ofrecer comandos estándar que se deben colocar en una barra de herramientas.  
  
-   Use una barra de información en lugar de un cuadro de diálogo modal.  
  
-   Cree un mensaje fuera de una ventana flotante.  
  
-   Usar varias de las barras de información en varias ubicaciones dentro de la misma ventana.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>¿Se pueden mostrar las barras de información de varias al mismo tiempo?  
 Sí, pueden mostrar las barras de información de varias al mismo tiempo. Se mostrará en orden de antigüedad, llegada con la primera barra de información que se muestra en las barras de información adicional y superior que se muestra a continuación.  
  
 El usuario verá un máximo de tres barras de información a la vez, después de que, si existen más barras de información, la región de la barra de información se convertirá en desplazable.  
  
### <a name="creating-an-infobar"></a>Creación de una barra de información  
 La barra de información tiene cuatro secciones, de izquierda a derecha:  
  
-   **Icono:** aquí es donde se agrega cualquier icono gustaría que se muestra en la barra de información, como un icono de advertencia.  
  
-   **Texto:** puede agregar texto para describir el usuario escenario/situación es, junto con vínculos en el texto, si es necesario. Recuerde que el texto concisa.  
  
-   **Acciones:** esta sección debe contener vínculos y botones de las acciones que el usuario puede realizar en la barra de información.  
  
-   **Botón Cerrar:** la última sección a la derecha puede tener un botón Cerrar.  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>Creación de una barra de información estándar en código administrado  
 La clase InfoBarModel puede usarse para crear un origen de datos para una barra de información. Utilice uno de estos cuatro constructores:  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
```  
  
 Este es un ejemplo que crea un InfoBarModel con algo de texto con un hipervínculo, un botón de acción y un icono.  
  
 ![Barra de información con hipervínculo](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 02_InfobarHyperlink")  
  
```  
var infoBar = new InfoBarModel(  
    textSpans: new[]  
    {  
        new InfoBarTextSpan("This is a "),  
        new InfoBarHyperlink("hyperlink"),  
        new InfoBarTextSpan(" InfoBar.")  
    },  
    actionItems: new[]  
    {  
        new InfoBarButton("Click Me")  
    },  
    image: KnownMonikers.StatusInformation,  
    isCloseButtonVisible: true);  
  
```  
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>Creación de una barra de información estándar en código nativo  
 Implementar la interfaz IVsInfoBar el fin de proporcionar una barra de información desde el código nativo.  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Obtención de un elemento de IU de la barra de información de una barra de información  
 La implementación de InfoBarModel o IVsInfoBar son modelos de datos que deben convertirse en un elemento de IU para que se muestre en la interfaz de usuario. Un UIElement se puede recuperar con el servicio SVsInfoBarUIFactory/IVsInfoBarUIFactory.  
  
```  
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)  
{  
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;  
    if (infoBarUIFactory == null)  
    {  
        uiElement = null;  
        return false;  
    }  
  
    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);  
    return uiElement != null;  
}  
```  
  
### <a name="placement"></a>Ubicación  
 Las barras de información se pueden mostrar en una o varias de las siguientes ubicaciones:  
  
-   Ventanas de herramientas  
  
-   Dentro de una pestaña de documento  
  
> [!IMPORTANT]
>  Es posible colocar una barra de información para proporcionar un mensaje sobre el contexto global. Debería aparecer entre las barras de herramientas y el cuadro de documento. No se recomienda porque provoca problemas con "saltar y tirón" del IDE y se deben evitar a menos que sea absolutamente necesario y apropiado.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Colocar una barra de información en un ToolWindowPane  
 El método ToolWindowPane.AddInfoBar(IVsInfoBar) puede usarse para agregar una barra de información a una ventana de herramientas. Esta API puede agregar un IVsInfoBar (de qué InfoBarModel es una implementación predeterminada), o un IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Colocar una barra de información en un documento o que no sean de ToolWindowPane  
 Para colocar una barra de información en cualquier IVsWindowFrame, utilice la propiedad VSFPROPID_InfoBarHost para obtener el IVsInfoBarHost para el marco y, a continuación, agregue el elemento de IU de la barra de información.  
  
```  
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)  
{  
    IVsInfoBarHost infoBarHost;  
    if (TryGetInfoBarHost(frame, out infoBarHost))  
    {  
        infoBarHost.AddInfoBar(uiElement);  
    }  
}  
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)  
{  
    object infoBarHostObj;  
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))  
    {  
        infoBarHost = null;  
        return false;  
    }  
  
    infoBarHost = infoBarHostObj as IVsInfoBarHost;  
    return infoBarHost != null;  
}  
  
```  
  
#### <a name="placing-an-infobar-in-the-main-window"></a>Colocar una barra de información en la ventana principal  
 Para colocar una barra de información en la ventana principal, use el VSSPROPID_MainWindowInfoBarHost del servicio IVsShell para obtener IVsInfoBarHost la ventana principal y, a continuación, agregarle la barra de información UIElement.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>¿Se sabe cuándo el usuario realiza la acción en mi barra de información?  
 Sí, se devolverá cada acción de evento al autor de la barra de información. Depende, a continuación, el autor de la barra de información para tomar medidas en el IDE según la selección del usuario en la barra de información. Se quitará automáticamente las barras de información desde el host se hizo clic en el botón Cerrar cuyo, pero se requiere trabajo adicional si otra barras de información deben desinstalarse después de cerrar. Telemetría también se deberá haber iniciado sesión por separado cada barra de información.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Recepción de eventos de la barra de información en un ToolWindowPane  
 ToolWindowPane tiene dos eventos para las barras de información. Se provoca el evento InfoBarClosed cuando se cierra una barra de información en el ToolWindowPane. El evento InfoBarActionItemClicked se genera cuando se hace clic en un hipervínculo o botón dentro de la barra de información.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Recibir eventos de la barra de información directamente desde el UIElement  
 IVsInfoBarUIElement.Advise puede utilizarse para suscribirse a eventos directamente desde el elemento de IU de una barra de información. Implementar IVsInfoBarUIEvents permitirá que el autor del cierre de recepción y haga clic en eventos.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a> Validación de errores  
 Cuando un usuario escribe la información que no es aceptable, por ejemplo, cuando se omite un campo obligatorio o cuando se insertan datos en un formato incorrecto, es mejor usar validación de un control o comentarios cerca del control en lugar de usar un cuadro de diálogo de error emergente bloqueo.  
  
### <a name="field-validation"></a>Validación de campos  
 Validación de formulario y el campo consta de tres componentes: un control, un icono y una información sobre herramientas. Aunque pueden usar varios tipos de controles de esto, se utilizará un cuadro de texto como un ejemplo.  
  
 ![Validación de campo &#40;en blanco&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 01_FieldValidation")  
  
 Si el campo es obligatorio, debe haber que indica el texto de marca de agua  **\<requiere >** y el fondo del campo debe ser ligero amarillo (VSColor: `Environment.ControlEditRequiredBackground`) y de primer plano debería ser gris (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Campo de validación con la etiqueta "Required"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 02_FieldValidationRequired")  
  
 El programa puede determinar que el control está en un estado de *contenido no válido especificado* cuando se mueve el foco a otro control o cuando el usuario hace clic en un botón de confirmación [Aceptar] o cuando el usuario guarda el documento o formulario.  
  
 Cuando se determina el estado de contenido no válido, aparece un icono dentro del control o simplemente está junto a ella. Información sobre herramientas que describe el error debe aparecer al mantener el mouse del icono o el control. Además, debe aparecer un borde de 1 píxel alrededor del control que está creando el estado no válido.  
  
 ![Especificaciones de diseño de validación de campo](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 03_LayoutSpecs")  
  
 **Especificaciones de diseño para la validación de campo**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Variaciones aceptables para la ubicación del icono  
 Existen innumerables casos particulares en los que los usuarios necesitan para mantenerse informado sobre los errores de validación. Teniendo en cuenta el tipo de control y configuración de la interfaz de usuario, elija la ubicación del icono adecuada para su situación.  
  
 ![Ubicaciones aceptables para la ubicación del icono](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 04_IconLocation")  
  
 **Variaciones aceptables para las ubicaciones de icono de validación de campo**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Necesidad de ida y vuelta a una conexión de red o el servidor de validación  
 En algunos casos, es necesario un ida y vuelta al servidor para comprobar el contenido y sería importante mostrar el progreso del usuario, comprobado y los Estados de error. La ilustración siguiente se muestra un ejemplo de este caso y la interfaz de usuario recomendada.  
  
 ![Validación que implica un viaje de ida a un servidor](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 05_RoundTrip")  
  
 **Validación que implica un viaje de ida a un servidor**  
  
 Tenga en cuenta que se debe proporcionar suficiente espacio disponible a la derecha del control con el fin de dar cabida al texto "..." Comprobando"y"Reintentar".  
  
#### <a name="in-place-warning-text"></a>Texto de advertencia en contexto  
 Cuando hay espacio disponible para colocar el mensaje de error cerca del control en un estado de error, esto es preferible al uso de la información sobre herramientas por sí solo.  
  
 ![En&#45;colocar advertencia](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 06_InPlaceWarning")  
  
 **Texto de advertencia en contexto**  
  
#### <a name="watermarks"></a>Marcas de agua  
 A veces un control completo o la ventana está en estado de error. En esta situación, utilice una marca de agua para indicar el error.  
  
 ![Watermark](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")  
  
 **Validación de campos de marca de agua**