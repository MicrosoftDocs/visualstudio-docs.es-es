---
title: "Las notificaciones y el progreso de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Las notificaciones y el progreso de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="a-namebkmknotificationsystemsa-notification-systems"></a><a name="BKMK_NotificationSystems"></a> Sistemas de notificación  
  
### <a name="overview"></a>Información general  
 Hay varias maneras de informar al usuario de lo que ocurre en Visual Studio con respecto a sus tareas de desarrollo de software.  
  
 Al implementar algún tipo de notificación:  
  
-   **Mantener el número de notificaciones al mínimo** número efectivo. Mensajes de notificación se deben aplicar a la mayoría de los usuarios de Visual Studio o a los usuarios de un área de característica o función específica. El uso excesivo de notificaciones puede sidetrack el usuario o disminuyan percibido facilidad de uso del sistema.  
  
-   **Asegúrese de que va a presentar mensajes claros y procesables** que el usuario puede utilizar para invocar el contexto adecuado para tomar decisiones más complejas y realizar una acción posterior.  
  
-   **Presentar mensajes sincrónicos y asincrónicos adecuadamente.** Notificaciones sincrónico indican que algo requiere atención inmediata, como cuando se bloquea un servicio web o un código de excepción. El usuario debe estar informado de esas situaciones inmediatamente de manera que requiera su entrada, como un cuadro de diálogo modal. Notificaciones asincrónicas son las que el usuario debe conocer, pero no estará obligado a actuar inmediatamente, como cuando se completa una operación de generación o una implementación de sitios web finaliza. Esos mensajes deben estar más ambiente y sin interrumpir el flujo de tareas del usuario.  
  
-   **Utilice el cuadro de diálogo modal sólo cuando sea necesario para evitar que el usuario realizar una acción posterior** antes de confirmar el mensaje o tomar una decisión que se presentan en el cuadro de diálogo.  
  
-   **Quitar notificaciones ambientales cuando ya no son válidos.** Es necesario descartar una notificación si ya han tomado medidas para solucionar el problema que se notifica al usuario.  
  
-   **Tenga en cuenta que las notificaciones pueden provocar las correlaciones falsas.** Los usuarios podrían creer que uno o varios de sus acciones activó una notificación cuando en realidad no hay ninguna relación. Ser claro en el mensaje de notificación sobre el contexto, el desencadenador y el origen de la notificación.  
  
### <a name="choosing-the-right-method"></a>Selección del método adecuado  
 Utilice esta tabla para ayudarle a elegir el método adecuado para notificar al usuario del mensaje.  
  
|Método|Uso|No use|  
|------------|---------|----------------|  
|[Cuadros de diálogo de mensaje de error modal](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Se utiliza cuando se necesita una respuesta del usuario antes de continuar.|No utilice cuando no es necesario para impedir que el usuario y su flujo de interrupción. Evite usar cuadros de diálogo modales, si es posible mostrar el mensaje de otra manera menos intrusivo.|  
|[Barra de estado IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Se utiliza cuando no hay información de texto ambiente relativos al estado de un proceso.|No utilice por sí solo. Se usa mejor junto con otro mecanismo de comentarios.|  
|[Barra de información incrustada](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|En una ventana de herramientas o la ventana de documento, use para la notificación de progreso, estado de error, resultados o información procesable.|No utilice la información no es relevante para la ubicación donde se ubica la barra de información.<br /><br /> No utilice fuera de una ventana de documento o herramienta.|  
|[Cursor del mouse cambia](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Puede utilizarse para notificar que un proceso está ocurriendo. También se utiliza para notificar que hay un cambio de estado en el mouse, como cuando arrastrar y colocar está en curso o el cursor del mouse está en un modo determinado, como el modo de dibujo.|No realice cambios de curso breve o si aleteo de cursor es probable (por ejemplo, cuando se vincula a las partes de un proceso en ejecución más tiempo en lugar de a todo el proceso).|  
|[Indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Se utiliza cuando se necesita para notificar el progreso (determinado o indeterminado). Hay una variedad de tipos de indicador de progreso y de uso específicos para cada uno. Consulte [indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Ventana de Visual Studio notificaciones](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La ventana de notificaciones no es públicamente extensible. Sin embargo, sirve para comunicarse en un intervalo de mensajes acerca de Visual Studio, incluidos los problemas críticos con su licencia y notificaciones de actualizaciones a Visual Studio o a paquetes.|No utilice para otros tipos de notificaciones.|  
|[Lista de errores](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Cuando el problema se relaciona directamente con la solución actualmente abierta del usuario tiene un problema (error/advertencia/información), deben realizar acciones en el código.<br /><br /> Esto podría incluir, por ejemplo:<br /><br /> -Mensajes del compilador (error/advertencia/información)<br /><br /> -Mensajes de analizador y diagnóstico código sobre el código<br /><br /> -Crear mensajes<br /><br /> Puede ser adecuado para problemas relacionados con los archivos de proyecto o solución, pero considere la posibilidad de una indicación del explorador de soluciones en primer lugar.|No utilice los elementos que no tienen ninguna relación con el código del usuario solución abierta.|  
|Notificaciones del Editor: bombilla|Utilícelo cuando disponga de una corrección disponible para solucionar un problema que existe en el archivo abierto.<br /><br /> Tenga en cuenta que también se debe usar la bombilla para hospedar acciones rápidas que se realizan en el código del usuario a petición, como refactorizaciones, pero en ese caso no aparecerán "estilo de notificación".|No utilice los elementos que no tienen ninguna relación al archivo abierto.|  
|Notificaciones del Editor: subrayados ondulados|Utilice esta opción para alertar al usuario a un problema con un intervalo determinado de su código abierto (por ejemplo, un subrayado rojo errores).|No se utilice para los elementos que no están relacionadas con un determinado intervalo de su código abierto.|  
|[Barras de estado incrustada](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Utilice esta opción para proporcionar el estado relacionado con el contenido o proceso en el contexto de una ventana de herramienta específica, ventana de documento o ventana de diálogo.|No utilice notificaciones general de productos, procesos o elementos que no tienen ninguna relación con el contenido dentro de la ventana concreta.|  
|[Notificaciones de la Bandeja de Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Usar para las notificaciones de procesos fuera de proceso de la superficie o complementario de aplicaciones.|No se utilice para las notificaciones que son relevantes para el IDE.|  
|[Burbujas de notificación](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Usar para notificar un proceso remoto o cambiar **fuera** del IDE.|No se use como un medio para notificar al usuario de los procesos **en** el IDE.|  
  
### <a name="notification-methods"></a>Métodos de notificación  
  
####  <a name="a-namebkmkmodalerrormessagedialogsa-modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Cuadros de diálogo de mensaje de error modal  
 Un cuadro de diálogo de mensaje de error modal se utiliza para mostrar un mensaje de error que requiere la confirmación o la acción del usuario.  
  
 ![Mensaje de error modal](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")  
  
 **Un cuadro de diálogo de mensaje de error modal avisa al usuario de una cadena de conexión no válida para una base de datos**  
  
####  <a name="a-namebkmkidestatusbara-ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> Barra de estado IDE  
 La probabilidad de que los usuarios Observe el texto de la barra de estado depende de su experiencia de equipo completo y la experiencia específica con la plataforma Windows. La base de clientes de Visual Studio tiende a ser expertos en ambas áreas, aunque los usuarios de Windows expertos incluso podrían perder los cambios en la barra de estado. Por lo tanto, la barra de estado se usa mejor con fines informativos o como una pila redundante para presenta información en otro lugar. Debe especificar cualquier tipo de información crítica que el usuario debe resolver inmediatamente en un cuadro de diálogo o en la ventana de herramienta de notificaciones.  
  
 La barra de estado de Visual Studio está diseñada para permitir varios tipos de información que se mostrará. Se divide en regiones para comentarios, diseñador, barra de progreso, animación y cliente.  
  
 El área de comentarios y la región del diseñador siempre están visibles. La barra de progreso y la animación regiones siempre son dinámicas y se basa en el contexto de usuario. La región del diseñador tiene un ancho estático determinado por la longitud de la cadena que se extrae de un recurso para el mensaje de texto que lo acompaña. Esto permite la localización ajustar el ancho sin necesidad de un cambio de código. Inglés, el ancho de esta cadena es de aproximadamente 220 píxeles. La región del diseñador se comportará normalmente y la región de comentarios absorba el espacio restante.  
  
 La barra de estado también se colorea para agregar interés visual y el valor funcional comunicándose varios cambios de estado IDE, como cuando el IDE está en modo de depuración.  
  
 ![Cambios de color de la barra de estado IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")  
  
 **Colores de barra de estado IDE**  
  
####  <a name="a-namebkmkembeddedinfobara-embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Barra de información incrustada  
 Una barra de información se puede utilizar en la parte superior de una ventana de documento o ventana de herramientas para informar al usuario de un estado o condición. También puede ofrecer comandos para que el usuario puede tener una manera de realizar acciones fácilmente. La barra de información es un control de shell estándar. Evite crear los suyos propios, que actuará y aparecen incoherente con otras personas en el IDE. Consulte [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) para detalles de implementación e instrucciones de uso.  
  
 ![Barra de información incrustada](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")  
  
 **Una barra de información incrustada en una ventana de documento, avisa al usuario que el IDE está en modo de depuración histórico y el editor no responde de la misma manera como lo hace en modo de depuración estándar.**  
  
####  <a name="a-namebkmkmousecursorchangesa-mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Cursor del mouse cambia  
 Al cambiar el cursor del mouse, utilice colores que están asociados al servicio VSColor y ya están asociados con el cursor. Cursor cambia puede utilizarse para indicar una operación en curso, así como las zonas donde el usuario se desplaza sobre un destino que puede arrastrar, colocar en o se utiliza para seleccionar un objeto de aciertos.  
  
 Use el cursor de espera de disponibilidad o solo si se debe reservar todo el tiempo de CPU disponible para una operación, lo que impide que el usuario expresar cualquier entrada adicional. En la mayoría de los casos con aplicaciones bien diseñadas con subprocesamiento múltiple, es frecuentes veces cuando los usuarios no podrán realizar otras operaciones.  
  
 Tenga en cuenta que el cursor cambia es útil tal como presenta una indicación de información redundante en otro lugar. No confíe en un cambio de cursor como la forma de comunicarse con el usuario, especialmente cuando intenta transmitir algo único que es fundamental que el usuario debe resolver.  
  
####  <a name="a-namebkmknotsysprogressindicatorsa-progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Indicadores de progreso  
 Indicadores de progreso son importantes para ofrecer al usuario información durante los procesos que tienen más de unos segundos en completarse. Se pueden mostrar indicadores de progreso en contexto (cerca del punto inicial de la acción en curso), en una barra de estado incrustada, en un cuadro de diálogo modal o en la barra de estado de Visual Studio. Siga las instrucciones en [indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) respecto a su uso e implementación.  
  
####  <a name="a-namebkmkvsnotificationstoolwindowa-visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Ventana de Visual Studio notificaciones  
 La ventana de notificaciones de Visual Studio notifica a los desarrolladores acerca de licencias, entorno (Visual Studio), extensiones y actualizaciones. Los usuarios pueden descartar notificaciones individuales o pueden optar por omitir ciertos tipos de notificaciones. La lista de notificaciones omitidas se administra en un **Herramientas > Opciones de** página.  
  
 La ventana de notificaciones no es extensible actualmente.  
  
 ![Ventana de notificaciones de Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")  
  
 **Ventana de herramientas de Visual Studio notificaciones**  
  
####  <a name="a-namebkmkerrorlista-error-list"></a><a name="BKMK_ErrorList"></a> Lista de errores  
 Una notificación en la lista de errores indica errores y advertencias que se produjeron durante la compilación o y proceso de compilación y permite al usuario navegar en el código de error específico del código.  
  
 ![Lista de errores](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")  
  
 **Lista de errores en Visual Studio**  
  
####  <a name="a-namebkmkembeddedstatusbarsa-embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Barras de estado incrustada  
 Dado que la barra de estado IDE es dinámica, con su contexto del área de cliente establecido en la ventana del documento activo y la información de actualización en el contexto del usuario y las respuestas del sistema, es difícil mantener una presentación continua de información o proporcionar el estado en los procesos asincrónicos a largo plazo. Por ejemplo, la barra de estado IDE no es adecuada para las notificaciones de los resultados de la ejecución de pruebas de múltiples ejecuciones o las selecciones de elementos de requerir una acción inmediata. Es importante conservar dicha información de estado en el contexto de la ventana de documento o herramienta que el usuario realiza una selección o inicia un proceso.  
  
 ![Barra de estado incrustada](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")  
  
 **Barra de estado incrustada en Visual Studio**  
  
####  <a name="a-namebkmkwindowstraya-windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Notificaciones de la Bandeja de Windows  
 El área de notificación está al lado del sistema de Windows del reloj en la barra de tareas de Windows. Muchas herramientas y componentes de software proporcionan iconos de esta área para que el usuario pueda obtener un menú contextual para las tareas de todo el sistema, como cambiar la resolución de pantalla o de obtención de actualizaciones de software.  
  
 Notificaciones de nivel de entorno deben ser mostradas en el centro de notificaciones de Visual Studio, no el área de notificación de Windows.  
  
####  <a name="a-namebkmknotificationbubblesa-notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Burbujas de notificación  
 Burbujas de notificaciones pueden aparecer como informativo en un editor o diseñador o como parte del área de notificación de Windows. El usuario percibe estos burbujas como los problemas que pueden resolver más tarde, que es una ventaja para las notificaciones no críticas. Burbujas son apropiadas para la información crítica que el usuario debe solucionar de inmediato. Si utiliza las burbujas de notificación en Visual Studio, siga el [orientación de escritorio de Windows para las burbujas de notificación](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx).  
  
 ![Burbuja de notificación](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")  
  
 **Burbuja de notificación en el área de notificación de Windows usada para Visual Studio**  
  
##  <a name="a-namebkmkprogressindicatorsa-progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Indicadores de progreso  
  
### <a name="overview"></a>Información general  
 Indicadores de progreso son una parte importante de un sistema de notificación para enviar los comentarios de usuario. Indican el usuario cuando se completará procesos y operaciones. Tipos de indicador familiar incluyen barras de progreso, giro cursores e iconos animados. El tipo y la ubicación de un indicador de progreso depende el contexto, incluyendo lo que se está informando y cuánto tiempo el proceso u operación tardará en completarse.  
  
#### <a name="factors"></a>Factores  
 Para determinar qué tipo de indicador es adecuado, debe determinar los factores siguientes.  
  
1.  **Tiempo:** cantidad de tiempo que tardará la operación  
  
2.  **Modalidad:** Si la operación es modal en el entorno (la interfaz de Usuario hasta que finalice el proceso de bloqueos)  
  
3.  **Persistent/transitorio:** Si el resultado final del progreso debe ser notificado o visible en un momento posterior  
  
4.  **Determinado o indeterminado:** Si se pueden calcular la hora de finalización de la operación y el progreso  
  
5.  **Ubicación del gráfico o Textual:** Si el progreso o el proceso está capturado en línea, en el cuerpo de un mensaje o un control específico, como el control de árbol  
  
6.  **Proximidad:** Si el progreso debe ser cerca de la interfaz de Usuario que está relacionado. ¿(Por ejemplo, puede ser en la barra de estado, que puede ser muy lejos, o es necesario que junto al botón que inicia el proceso)?  
  
#### <a name="determinate-progress"></a>Progreso determinada  
  
|Tipo de curso|Cuándo y cómo se utiliza|Notas|  
|-------------------|-------------------------|-----------|  
|Barra de progreso (determinada)|Duración de esperada > 5 segundos.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**No** Insertar texto en la animación.|  
|Barra de información|Mensajería asociado con la interfaz de Usuario contextual. Consulte [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**No** usar varios infobars cuando sea necesario indicar varios procesos. Utilice las barras de progreso apiladas en su lugar.|  
|Resultados (Ventana)|Notificación transitorio: proceso de nivel de aplicación que el usuario desea **revisar** Detalles de después de la finalización.|**No** usar si el usuario tendrá que hacer referencia a los datos más adelante.|  
|Archivo de registro|Empareja con notificación intransient en los casos cuando es importante **Guardar** detalles después de la finalización.||  
|Barra de estado|Notificación transitorio: proceso de nivel de aplicación que el usuario hará **no necesita** Detalles de después de la finalización.<br /><br /> Incluye una barra de progreso incrustado.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||  
  
#### <a name="indeterminate-progress"></a>Progreso indeterminada  
  
|Tipo de curso|Cuándo y cómo se utiliza|Notas|  
|-------------------|-------------------------|-----------|  
|Barra de progreso (indeterminado)|Duración de esperada > 5 segundos.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**No** Insertar texto en la animación.|  
|Hormigas (puntos horizontales animados)|Ida y vuelta al servidor.<br /><br /> Coloca el punto cercano de contexto en la parte superior del contenedor primario.|**No** use si no secundario de ningún contenedor completo.|  
|Spinner (anillo de progreso)|Proceso asociado a interfaz de Usuario contextual, donde el espacio es una consideración.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||  
|Barra de información|Mensajería asociado con la interfaz de Usuario contextual. Consulte [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**No** usar varios infobars cuando sea necesario indicar varios procesos. Utilice las barras de progreso apiladas en su lugar.|  
|Resultados (Ventana)|Notificación transitorio: proceso de nivel de aplicación que el usuario desee **revisar** Detalles de después de la finalización.|**No** utilice para la información que necesita conservar entre sesiones.|  
|Archivo de registro|Empareja con notificación intransient en los casos cuando es importante **Guardar** detalles después de la finalización.||  
|Barra de estado|Notificación transitorio: proceso de nivel de aplicación que el usuario hará **no necesita** Detalles de después de la finalización.<br /><br /> Incluye la barra de progreso incrustado.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||  
  
### <a name="progress-indicator-types"></a>Tipos de indicador de progreso  
  
#### <a name="progress-bars"></a>Barras de progreso  
  
##### <a name="indeterminate"></a>Indeterminado  
 ![Barra de progreso indeterminada](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")  
  
 **Barra de progreso indeterminada**  
  
 "Indeterminado" significa que todo el progreso de una operación o no se puede determinar el proceso. Utilice las barras de progreso indeterminada para operaciones que requieren una cantidad ilimitada de tiempo o que tienen acceso a un número desconocido de objetos. Utilice una descripción textual para acompañar a lo que está sucediendo. Utilizar tiempos de espera para dar a límites a las operaciones de tiempo. Barras de progreso indeterminada utilice animaciones para mostrar que se está realizando el progreso pero no proporcionar ninguna otra información. No elija una barra de progreso indeterminada basándose únicamente en la posible falta de precisión por sí solo.  
  
##### <a name="determinate"></a>Determinada  
 ![Barra de progreso determinada](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")  
  
 **Barra de progreso determinada**  
  
 "Determinado" significa que una operación o un proceso requiere una cantidad limitada de tiempo, incluso si esa cantidad de tiempo no se puede predecir con exactitud. Indica claramente que ha completado. No permita que una barra de progreso vaya al 100 por ciento, a menos que se haya completado la operación. Animación de la barra de progreso determinada mueve de izquierda a derecha de 0 a 100%.  
  
 Nunca, mueva el indicador de progreso con versiones anteriores durante una operación. La barra debe avanzar continuamente cuando comience la operación y alcanzar el 100% cuando termina. El punto de la barra de progreso es dar al usuario una idea de cuánto tarda de toda la operación, independientemente de cuántos pasos implicados.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Simultáneas reporting (barras de progreso apiladas)  
 Si una operación tardará mucho tiempo, quizás pueden utilizarse varios minutos, a continuación, barras de progreso de dos, uno que muestra el progreso general para una operación y otro para la progresión del paso actual. Por ejemplo, si un programa de instalación está copiando muchos archivos, puede utilizar una barra de progreso para indicar cuánto tiempo todo el proceso tarda un segundo puede indicar qué porcentaje del archivo o directorio que se va a copiar. No informan de más de cinco operaciones simultáneas o procesos mediante barras de progreso apiladas. Si tiene más de cinco operaciones simultáneas o procesos de informes, utilice un cuadro de diálogo modal con un botón Cancelar e informar los detalles de progreso en la ventana de salida.  
  
##### <a name="textual-descriptions"></a>Descripciones de texto  
 Utilice una descripción textual para acompañar a lo que ocurre y el tiempo estimado para finalización. Si es imposible determinar cuánto tardará una operación, una mejor opción para enviar comentarios podría ser un icono animado en lugar de una barra de progreso.  
  
 Visual Studio proporciona una barra de progreso estándar en la barra de estado que se puede utilizar cualquier producto integrado en Visual Studio. Para obtener descripciones textuales de lo que sucede mientras se anima la barra de progreso, puede actualizarse el texto de la barra de estado.  
  
#### <a name="other-progress-indicators"></a>Otros indicadores de progreso  
  
##### <a name="ants-animated-horizontal-dots"></a>Hormigas (puntos horizontales animados)  
 ![Hormigas de progreso](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")  
  
 "Las hormigas," animados puntos horizontales, proporciona una referencia visual para un proceso de servidor de ida y vuelta indeterminado.  
  
##### <a name="spinner-progress-ring"></a>Spinner (anillo de progreso)  
 ![Control giratorio de progreso](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")  
  
 El control de número (también conocido como un "anillo de progreso") es un indicador de progreso indeterminada que se utiliza principalmente en relación con la interfaz de Usuario contextual. Mostrar una rueda cerca de su contenido relacionado, como un encabezado de categoría textual, mensajería o control.  
  
##### <a name="cursor-feedback"></a>Información del cursor  
 Para las operaciones que tardar entre 2 a 7 segundos, proporcionar comentarios de cursor. Normalmente, esto significa que con el cursor de espera proporcionado por el sistema operativo. Para obtener instrucciones, consulte el artículo de MSDN [Cursors.Wait propiedad](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx).  
  
#### <a name="progress-indicator-locations"></a>Ubicaciones de indicador de progreso  
  
##### <a name="status-bar"></a>Barra de estado  
 La barra de estado proporciona un lugar para mostrar mensajes e información útil al usuario sin interrumpir el trabajo del usuario a la aplicación. Estado de progreso aparece normalmente en la parte inferior de una ventana, será un panel de información sobre herramientas que incluye un mensaje acerca de la medida del progreso en combinación con un indicador de la barra de progreso.  
  
 ![Barra de estado con barra de progreso](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")  
  
 **Barra de estado con barra de progreso**  
  
 ![Barra de estado con mensajes](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")  
  
 **Barra de estado con la descripción textual**  
  
##### <a name="infobar"></a>Barra de información  
 Es similar a la barra de estado, la barra de información proporciona notificación contextual y mensajería, que también se pueden emparejar con indicadores de progreso indeterminada como la barra de progreso o control de giro. La barra de información no debe proporcionar progreso nivel granular o indicación de progreso determinada. Consulte [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Barra de información con barra y mensajes de progreso](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")  
  
 **Barra de información con barra de progreso y la descripción textual**  
  
 ![Barra de información dentro de una ventana](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")  
  
 **Barra de información dentro de la ventana de análisis de código**  
  
##### <a name="inline"></a>Alineado  
 Indicación del progreso en línea se puede representar cualquiera de los tipos de cargador de progreso. El indicador de progreso se empareja normalmente con la mensajería, pero esto no es un requisito.  
  
 ![Control giratorio de progreso en línea](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")  
  
 **Control de giro que se combina con una descripción textual**  
  
 ![Barras de progreso apiladas en línea](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")  
  
 **Barras de progreso apiladas determinada**  
  
 ![Mensajes de progreso en línea](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")  
  
 **Texto de Server Explorer en línea: la actualización...**  
  
##### <a name="tool-windows"></a>Ventanas de herramientas  
 Indicación del progreso global está representado por una barra de progreso indeterminada situada directamente debajo de la barra de herramientas.  
  
 ![Barra de progreso indeterminada global](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")  
  
 **Barra de progreso indeterminada global de Team Explorer**  
  
##### <a name="dialogs"></a>Cuadros de diálogo  
 Los cuadros de diálogo pueden contener cualquiera de los tipos de cargador de progreso. Indicadores de progreso pueden se empareja con mensajería así como combinar con varios niveles de indicación de progreso para representar granular y procesos de sub.  
  
 ![Cuadro de diálogo con varios tipos de indicador de progreso](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")  
  
 **Cuadro de diálogo de Visual Studio con procesos simultáneos y varios tipos de indicador de progreso**  
  
 ![Cuadro de diálogo con cargador y mensajes de progreso](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")  
  
 **Cuadro de diálogo de Visual Studio con cargador de progreso y mensajes en línea de comandos**  
  
##### <a name="document-well"></a>Documento bien  
 El documento también puede mostrar varios tipos de cargador de progreso en combinación con los controles.  
  
 ![Mensajes de progreso en la sección de documentos](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")  
  
 **Barra de progreso indeterminada por debajo de la barra de herramientas**  
  
##### <a name="output-window"></a>Resultados (Ventana)  
 La ventana de salida es adecuada para controlar la progresión del proceso y el estado de progreso a través de mensajes de texto en línea. Debe utilizar la barra de estado junto con los informes de progreso de ventana de salida.  
  
 ![Mensajes de progreso en la ventana de salida](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")  
  
 **Ventana de salida con el estado de proceso continuo y esperar de mensajería**  
  
##  <a name="a-namebkmkinfobarsa-infobars"></a><a name="BKMK_Infobars"></a> Infobars  
  
### <a name="overview"></a>Información general  
 Infobars ofrecer al usuario un indicador cerca de su punto de atención y mediante el control de barra de información compartida garantiza la coherencia en la apariencia visual y la interacción.  
  
 ![Barra de información](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")  
  
 **Infobars en Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>El uso apropiado de una barra de información  
  
-   Para proporcionar al usuario un mensaje de no bloqueo pero importante relevante para el contexto actual  
  
-   Para indicar que la interfaz de Usuario está en un estado determinado o una condición que tiene algunas implicaciones de interacción, como la depuración histórica  
  
-   Para notificar al usuario que el sistema ha detectado problemas, como cuando una extensión está causando problemas de rendimiento  
  
-   Para proporcionar al usuario una manera fácil realizar las acciones, como cuando el editor detecta que un archivo ha mixtas tabulaciones y espacios  
  
##### <a name="do"></a>Hacer:  
  
-   Mantenga el texto de mensaje de la barra de información cortas y al punto.  
  
-   Mantenga el texto de los vínculos y botones concisa.  
  
-   Asegúrese de que las opciones de "acción" proporcionar a los usuarios son mínimas, que muestra sólo las acciones necesarias.  
  
##### <a name="dont"></a>No:  
  
-   Usar una barra de información para ofrecer comandos estándar que se deben colocar en una barra de herramientas.  
  
-   Usar una barra de información en lugar de un cuadro de diálogo modal.  
  
-   Cree un mensaje fuera de una ventana flotante.  
  
-   Usar varios infobars en varias ubicaciones dentro de la misma ventana.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>¿Puede mostrar varias infobars al mismo tiempo?  
 Sí, puede mostrar varias infobars al mismo tiempo. Se mostrará en orden de antigüedad, primero en ser atendido con la primera barra de información que se muestra en infobars superior y adicionales que se muestra a continuación.  
  
 El usuario verá un máximo de tres infobars a la vez, después de que, si hay más infobars, la región de la barra de información se convertirá en desplazable.  
  
### <a name="creating-an-infobar"></a>Crear una barra de información  
 La barra de información tiene cuatro secciones, de izquierda a derecha:  
  
-   **Icono:** aquí es donde se agrega cualquier icono que le gustaría mostrar en la barra de información, como un icono de advertencia.  
  
-   **Texto:** puede agregar texto que describa el usuario escenario/situación en, junto con los vínculos en el texto, si es necesario. Recuerde que debe mantener el texto breve.  
  
-   **Acciones:** esta sección debe contener vínculos y botones de las acciones que puede realizar el usuario en la barra de información.  
  
-   **Botón Cerrar:** la última sección a la derecha puede tener un botón Cerrar.  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>Crear una barra de información estándar en código administrado  
 La clase InfoBarModel puede utilizarse para crear un origen de datos para una barra de información. Utilice uno de estos cuatro constructores:  
  
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
  
 Este es un ejemplo que crea una InfoBarModel con algo de texto con un hipervínculo, un botón de acción y un icono.  
  
 ![Barra de información con hipervínculo](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")  
  
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
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>Crear una barra de información estándar en código nativo  
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
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Obtención de una barra de información UIElement de una barra de información  
 La implementación de InfoBarModel o IVsInfoBar son modelos de datos que deben convertirse en un elemento de IU para que se muestre en la interfaz de Usuario. UIElement se puede recuperar con el servicio de SVsInfoBarUIFactory/IVsInfoBarUIFactory.  
  
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
 Infobars se pueden mostrar en una o varias de las siguientes ubicaciones:  
  
-   Ventanas de herramientas  
  
-   Dentro de una ficha de documento  
  
> [!IMPORTANT]
>  Es posible colocar una barra de información para proporcionar un mensaje sobre el contexto global. Debería aparecer entre las barras de herramientas y el documento bien. No se recomienda porque provoca problemas con "saltar y tirón" del IDE y debe evitarse, a menos que sea absolutamente necesario y apropiado.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Colocar una barra de información en un ToolWindowPane  
 El método ToolWindowPane.AddInfoBar(IVsInfoBar) puede utilizarse para agregar una barra de información a una ventana de herramientas. Esta API puede agregar una IVsInfoBar (de qué InfoBarModel es una implementación predeterminada), o un IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Colocar una barra de información en un documento o no ToolWindowPane  
 Para colocar una barra de información en cualquier IVsWindowFrame, utilice la propiedad VSFPROPID_InfoBarHost para obtener la IVsInfoBarHost para el marco y, a continuación, agregue la barra de información UIElement.  
  
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
 Para colocar una barra de información en la ventana principal, use la VSSPROPID_MainWindowInfoBarHost del servicio IVsShell para obtener IVsInfoBarHost de la ventana principal y, a continuación, agregarle la barra de información de UIElement.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>¿Se sabe cuando el usuario realiza la acción en la barra de información?  
 Sí, se devolverá cada acción de evento para el autor de la barra de información. A continuación, es el autor de la barra de información para tomar medidas en el IDE en función de selección de usuario en la barra de información. Infobars se quitará automáticamente desde el host cuyo cerrar botón se hizo clic, pero se requiere trabajo adicional si otro infobars deba quitarse después de cerrar. Telemetría también deberá registrarse de manera independiente por cada barra de información.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Recepción de eventos de la barra de información en un ToolWindowPane  
 ToolWindowPane tiene dos eventos para infobars. El evento InfoBarClosed se produce cuando se cierra una barra de información en el ToolWindowPane. El evento InfoBarActionItemClicked se genera cuando se hace clic en un hipervínculo o botón dentro de la barra de información.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Recepción de eventos de la barra de información directamente desde el UIElement  
 IVsInfoBarUIElement.Advise puede utilizarse para suscribirse a eventos directamente desde UIElement de una barra de información. Implementar IVsInfoBarUIEvents permite al autor del cierre de recepción y haga clic en eventos.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="a-namebkmkerrorvalidationa-error-validation"></a><a name="BKMK_ErrorValidation"></a> Validación de error  
 Cuando un usuario escribe la información que no es aceptable, por ejemplo, cuando se omite un campo obligatorio o cuando se insertan datos en un formato incorrecto, es mejor usar la validación de control o comentarios cerca del control en lugar de utilizar un cuadro de diálogo de error emergente bloqueo.  
  
### <a name="field-validation"></a>Validación de campos  
 Validación de formulario y el campo consta de tres componentes: un control, un icono y una información sobre herramientas. Aunque varios tipos de controles pueden usar esto, un cuadro de texto se utilizará como un ejemplo.  
  
 ![Validación de campo &#40; en blanco &#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")  
  
 Si el campo es obligatorio, debe haber texto que indica de marca de agua **\< necesarios>** y el fondo del campo debe ser ligero amarillo (VSColor: `Environment.ControlEditRequiredBackground`) y el primer plano debería ser gris (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Validación de campo con la etiqueta "Obligatorio"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")  
  
 El programa puede determinar que el control está en un estado de *contenido no válido especificado* cuando se desplaza el foco a otro control o cuando el usuario hace clic en un botón de confirmación [Aceptar] o cuando el usuario guarda el documento o formulario.  
  
 Cuando se determina el estado de contenido no válido, aparece un icono dentro del control o justo al lado. Debería aparecer una información sobre herramientas que describe el error de desplazamiento del icono o el control. Además, debe aparecer un borde de 1 píxel alrededor del control que está creando un estado no válido.  
  
 ![Especificaciones de diseño de validación de campo](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")  
  
 **Especificaciones de diseño para la validación de campo**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Variaciones aceptables para la ubicación del icono  
 Existen innumerables casos excepcionales en que los usuarios necesitan para mantenerse informado acerca de los errores de validación. Teniendo en cuenta el tipo de control y la configuración de la interfaz de Usuario, elija la ubicación del icono adecuada a su situación.  
  
 ![Ubicaciones aceptables para la ubicación del icono](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")  
  
 **Variaciones aceptables para las ubicaciones de icono de validación de campo**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Necesidad de ida y vuelta a una conexión de red o de servidor de validación  
 En algunos casos, es necesario ida y vuelta al servidor para comprobar el contenido y sería importante mostrar el progreso del usuario, comprobado y los Estados de error. La ilustración siguiente muestra un ejemplo de este caso y la interfaz de Usuario recomendada.  
  
 ![Validación que implica un viaje de ida y vuelta a un servidor](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")  
  
 **Validación que implica un viaje de ida a un servidor**  
  
 Tenga en cuenta que se debe proporcionar suficiente espacio disponible a la derecha del control con el fin de acomodar "Comprobar..." y el texto "Reintentar".  
  
#### <a name="in-place-warning-text"></a>Texto de la advertencia en contexto  
 Cuando hay espacio disponible para colocar el mensaje de error cerca del control en un estado de error, esto es preferible al uso de la información sobre herramientas por sí solo.  
  
 ![En &#45; advertencia contexto](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")  
  
 **Texto de la advertencia en contexto**  
  
#### <a name="watermarks"></a>Marcas de agua  
 A veces un control completo o la ventana está en estado de error. En esta situación, utilice una marca de agua para indicar el error.  
  
 ![Marca de agua](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")  
  
 **Validación de campos de marca de agua**