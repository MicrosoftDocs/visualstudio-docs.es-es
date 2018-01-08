---
title: Las notificaciones y el progreso de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0721d0080ec135a8e969cc420dfbb51e81ac4454
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="notifications-and-progress-for-visual-studio"></a>Las notificaciones y el progreso de Visual Studio
##  <a name="BKMK_NotificationSystems"></a>Sistemas de notificación  
  
### <a name="overview"></a>Información general  
 Hay varias maneras para informar al usuario lo que está sucediendo en Visual Studio con respecto a sus tareas de desarrollo de software.  
  
 Al implementar algún tipo de notificación:  
  
-   **Mantenga el número de notificaciones al mínimo** número efectivo. Mensajes de notificación se deben aplicar a la mayoría de los usuarios de Visual Studio o a los usuarios de un área de característica o función específica. El uso excesivo de notificaciones puede sidetrack el usuario o disminuir percibido facilidad de uso del sistema.  
  
-   **Asegúrese de que se va a presentar mensajes claras y procesables** que el usuario puede usar para invocar el contexto adecuado para tomar decisiones más complejos y realizar una acción posterior.  
  
-   **Presentar mensajes sincrónicos y asincrónicos adecuadamente.** Notificaciones sincrónicas indican que algo requiere atención inmediata, como cuando se bloquea un servicio web o un código de excepción. El usuario debe ser informado de esas situaciones inmediatamente de forma que requiera su entrada, como en un cuadro de diálogo modal. Las notificaciones asincrónicas son los que el usuario debe conocer, pero no estará obligado a actuar inmediatamente, como cuando se completa una operación de generación o una implementación de sitios web finaliza. Los mensajes deben ser más ambiente y no interrumpirá el flujo de tareas del usuario.  
  
-   **Use los cuadros de diálogo modales sólo cuando sea necesario para evitar que el usuario realizar una acción posterior** antes reconoce el mensaje o tomar una decisión que se presentan en el cuadro de diálogo.  
  
-   **Quitar las notificaciones de ambiente cuando ya no son válidos.** No requieren que el usuario descartar una notificación si ya han tomado medidas para solucionar el problema que se le notifique.  
  
-   **Tenga en cuenta que las notificaciones pueden provocar las correlaciones falsas.** Los usuarios que consideres que uno o varios de sus acciones se desencadenan una notificación cuando en realidad no hay ninguna relación causal. Ser claro en el mensaje de notificación sobre el contexto, el desencadenador y el origen de la notificación.  
  
### <a name="choosing-the-right-method"></a>Elegir el método correcto  
 Use esta tabla para ayudarle a elegir el método adecuado para notificar al usuario de su mensaje.  
  
|Método|Usar|No use|  
|------------|---------|----------------|  
|[Cuadros de diálogo de mensaje de error modal](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Se utiliza cuando se necesita una respuesta del usuario antes de continuar.|Debe usarse cuando no es necesario para impedir que el usuario y su flujo de interrupción. Evite usar los cuadros de diálogo modales si es posible mostrar el mensaje de manera menos intrusivo y otro.|  
|[Barra de estado del IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Se utiliza cuando hay ambiente información textual acerca del estado de un proceso.|No usar en solitario. Mejor usar junto con otro mecanismo de comentarios.|  
|[Barra de información incrustada](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|En una ventana de herramientas o ventana de documento, que se utiliza para notificar de progreso, estado de error, resultados o información procesable.|Debe usarse si la información no es relevante para la ubicación donde se coloca la barra de información.<br /><br /> No utilice fuera de una ventana de documento o herramienta.|  
|[Cursor del mouse cambia](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Puede utilizarse para notificar a los que un proceso está sucediendo. También se utiliza para notificar que hay un cambio de estado en el mouse, como cuando arrastrar y colocar está en curso o el cursor del mouse está en un modo determinado, como el modo de dibujo.|No realice cambios de progreso corto o si aleteo de cursor es probable (por ejemplo, cuando se vincula a las partes de un proceso en ejecución más largo en lugar de a todo el proceso).|  
|[Indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Se utiliza cuando necesita para notificar el progreso (determinado o indeterminado). Hay una variedad de tipos de indicadores de progreso y de uso específicos para cada uno. Vea [indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Ventana de Visual Studio notificaciones](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La ventana de notificaciones no es públicamente extensible. Sin embargo, se permite la comunicación un intervalo de mensajes sobre Visual Studio, incluidos los problemas críticos con sus licencias y notificaciones de actualizaciones a Visual Studio o a paquetes.|No debe usarse para otros tipos de notificaciones.|  
|[Lista de errores](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Cuando el problema se relaciona directamente con la solución actualmente abierta del usuario tiene un problema (error/advertencia/información), deben realizar acciones en el código.<br /><br /> Esto podría incluir, por ejemplo:<br /><br /> -Mensajes del compilador (error/advertencia/información)<br /><br /> -Mensajes de analizador/diagnóstico código sobre el código<br /><br /> -Mensajes de compilación<br /><br /> Puede ser adecuado para problemas relacionados con los archivos de proyecto o solución, pero tenga en cuenta una indicación del explorador de soluciones en primer lugar.|No debe usarse para los elementos que no tienen ninguna relación con el código del usuario solución abierta.|  
|Las notificaciones de editor: bombilla|Utilícelo cuando disponga de una corrección disponible para solucionar un problema que existe en el archivo abierto.<br /><br /> Tenga en cuenta que también se debe usar la bombilla para hospedar acciones rápidas que se han realizado en el código del usuario a petición, como refactorizaciones, pero en ese caso no aparecerá "estilo de notificación".|No debe usarse para los elementos que no tienen ninguna relación al archivo abierto.|  
|Las notificaciones de editor: subrayados ondulados|Utilice esta opción para avisar al usuario a un problema con un intervalo determinado de su código abierto (por ejemplo, un zigzag rojo si hay errores).|No debe usarse para los elementos que no hacen referencia a un intervalo determinado de su código abierto.|  
|[Barras de estado incrustada](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Se utiliza para proporcionar el estado relacionado con el contenido ni proceso en contexto de una ventana de herramientas específica, la ventana de documento o la ventana de diálogo.|No utilice para notificaciones de producto general, procesos o elementos que no tienen ninguna relación con el contenido dentro de la ventana concreta.|  
|[Notificaciones de la Bandeja de Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Usar para notificaciones para los procesos de fuera de proceso de superficie o complementarias de las aplicaciones.|No debe usarse para las notificaciones que son relevantes para el IDE.|  
|[Burbujas de notificación](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Usar para notificar a los de un proceso remoto o cambiar **fuera** del IDE.|No se use como un medio para notificar al usuario de procesos **en** el IDE.|  
  
### <a name="notification-methods"></a>Métodos de notificación  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a>Cuadros de diálogo de mensaje de error modal  
 Un cuadro de diálogo de mensaje de error modal se utiliza para mostrar un mensaje de error que requiere confirmación o la acción del usuario.  
  
 ![Mensaje de error modal](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "01_ModalErrorMessage 0901")  
  
 **Un cuadro de diálogo de mensaje de error modal alerta al usuario de una cadena de conexión no válida para una base de datos**  
  
####  <a name="BKMK_IDEStatusBar"></a>Barra de estado del IDE  
 La probabilidad de que los usuarios notificación de texto de la barra de estado está relacionado con su experiencia informática global y experiencia específica de la plataforma Windows. La base de clientes de Visual Studio tiende a ser con experiencia en ambas áreas, aunque los usuarios de Windows incluso experimentados podrían perder los cambios en la barra de estado. Por lo tanto, la barra de estado se utiliza mejor con fines informativos o como una indicación de redundancia de la información presenta en otro lugar. Debe especificar cualquier tipo de información crítica que el usuario debe resolver inmediatamente en un cuadro de diálogo o en la ventana de herramienta de notificaciones.  
  
 La barra de estado de Visual Studio está diseñada para permitir varios tipos de información que se mostrará. Se divide en regiones de comentarios, el diseñador, barra de progreso, animación y cliente.  
  
 La región de comentarios y la región del diseñador siempre están visibles. La barra de progreso y la animación regiones siempre son dinámicos y se basa en el contexto de usuario. La región del diseñador tiene un ancho estático determinado por la longitud de la cadena que se haya extraído de un recurso para el mensaje de texto que lo acompaña. Esto permite la localización cambiar el ancho sin necesidad de un cambio en el código. Para el inglés, el ancho de esta cadena es aproximadamente 220 píxeles. La región del diseñador se comportará normalmente y la región de comentarios absorba el espacio restante.  
  
 La barra de estado también se colorea para agregar interés visual y el valor funcional mediante una comunicación varios cambios de estado IDE, como cuando el IDE está en modo de depuración.  
  
 ![Cambios de color de la barra de estado IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "02_IDEStatusBar 0901")  
  
 **Colores IDE de la barra de estado**  
  
####  <a name="BKMK_EmbeddedInfobar"></a>Barra de información incrustada  
 Una barra de información se puede utilizar en la parte superior de una ventana de documento o ventana de herramientas para informar al usuario de un estado o condición. También pueden ofrecer comandos para que el usuario puede tener una manera de actuar fácilmente. La barra de información es un control de shell estándar. Evite crear el suyo propio, que actuará y aparecen incoherente con otras personas en el IDE. Vea [barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) para detalles de implementación e instrucciones de uso.  
  
 ![Incrustar barra de información](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "03_EmbeddedInfobar 0901")  
  
 **Una barra de información incrustada en una ventana de documento, el usuario que el IDE está en modo de depuración histórica y el editor no responde de la misma manera como se hace en modo de depuración estándar de alertas.**  
  
####  <a name="BKMK_MouseCursorChanges"></a>Cursor del mouse cambia  
 Al cambiar el cursor del mouse, utilice colores que están asociados al servicio VSColor y ya están asociadas con el cursor. Cambios de cursor pueden utilizarse para indicar una operación en curso, así como las zonas donde el usuario sitúa el mouse sobre un destino que se pueden arrastrar, coloca o utilizar para seleccionar un objeto de llamadas.  
  
 Use el cursor del mouse (ratón) de disponibilidad/espera solo cuando se debe reservar todo el tiempo de CPU disponible para una operación, impide que el usuario expresar cualquier entrada adicional. En la mayoría de los casos con aplicaciones bien escritas con subprocesamiento múltiple, es frecuentes veces cuando se impidieron que los usuarios realizar otras operaciones.  
  
 Tenga en cuenta que los cambios de cursor son útiles, tal como presenta una indicación redundancia para obtener información en otro lugar. No se basan en un cambio de cursor como el único método de comunicación con el usuario especialmente al intentar transmitir algo que es fundamental que el usuario debe resolver.  
  
####  <a name="BKMK_NotSysProgressIndicators"></a>Indicadores de progreso  
 Indicadores de progreso son importantes para enviar los comentarios de usuario durante los procesos que tarden más de unos segundos para completar. Se pueden mostrar los indicadores de progreso en contexto (cerca del punto inicial de la acción en curso), en una barra de estado incrustada, en un cuadro de diálogo modal o en la barra de estado de Visual Studio. Siga las instrucciones de [indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) con respecto a su uso e implementación.  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a>Ventana de Visual Studio notificaciones  
 La ventana de notificaciones de Visual Studio notifica a los desarrolladores sobre las licencias, entorno (Visual Studio), extensiones y actualizaciones. Los usuarios pueden descartar notificaciones individuales o pueden optar por omitir ciertos tipos de notificaciones. La lista de notificaciones omitidas se administra en un **Herramientas > opciones** página.  
  
 La ventana de notificaciones no está actualmente extensible.  
  
 ![Ventana de Visual Studio notificaciones](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "06_VSNotificationsWindow 0901")  
  
 **Ventana de herramientas de Visual Studio notificaciones**  
  
####  <a name="BKMK_ErrorList"></a>Lista de errores  
 Una notificación en la lista de errores indica errores y advertencias que se produjeron durante la compilación o y proceso de compilación y permite al usuario navegar en el código a ese error de código concretos.  
  
 ![Lista de errores](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "08_ErrorList 0901")  
  
 **Lista de errores en Visual Studio**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a>Barras de estado incrustada  
 Dado que la barra de estado IDE es dinámica, con su contexto de la región de cliente establecido en la ventana del documento activo y la información de actualización en el contexto del usuario o en las respuestas del sistema, resulta difícil de mantener una presentación continua de información o dé a estado en a largo plazo procesos asincrónicos. Por ejemplo, no es adecuada para las notificaciones de los resultados de la ejecución de pruebas de varias ejecuciones o elemento inmediatamente las selecciones de la barra de estado IDE. Es importante conservar dicha información de estado en el contexto de la ventana de documento o herramienta que el usuario realiza una selección o inicia un proceso.  
  
 ![Barra de estado incrustada](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "09_EmbeddedStatusBar 0901")  
  
 **Barra de estado incrustada en Visual Studio**  
  
####  <a name="BKMK_WindowsTray"></a>Notificaciones de la Bandeja de Windows  
 Las ventanas de área de notificación está al lado del sistema del reloj en la barra de tareas de Windows. Muchas herramientas y componentes de software proporcionan iconos de esta área para que el usuario puede obtener un menú contextual para tareas de todo el sistema, como cambiar la resolución de pantalla o la obtención de actualizaciones de software.  
  
 Las notificaciones de nivel de entorno deben aparecer en el centro de notificaciones de Visual Studio, no el área de notificación de Windows.  
  
####  <a name="BKMK_NotificationBubbles"></a>Burbujas de notificación  
 Las burbujas de notificación pueden aparecer como informativo dentro de un editor o diseñador o como parte del área de notificación de Windows. El usuario percibe estos burbujas como los problemas que se pueden resolver una versión posterior, que es una de las ventajas para las notificaciones no críticas. Burbujas son apropiadas para la información crítica que el usuario debe solucionar inmediatamente. Si utiliza las burbujas de notificación en Visual Studio, siga el [instrucciones de escritorio de Windows para las burbujas de notificación](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx).  
  
 ![Burbuja de notificación](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "07_NotificationBubbles 0901")  
  
 **Burbuja de notificación en el área de notificación de Windows que se utiliza para Visual Studio**  
  
##  <a name="BKMK_ProgressIndicators"></a>Indicadores de progreso  
  
### <a name="overview"></a>Información general  
 Indicadores de progreso son una parte importante de un sistema de notificación para enviar los comentarios del usuario. El usuario le informan cuando se completará los procesos y las operaciones. Tipos de indicadores familiarizado incluyen barras de progreso, los cursores de giro e iconos animados. El tipo y la ubicación de un indicador de progreso depende del contexto, incluidos lo que se está informando y cuánto tiempo el proceso u operación tardará en completarse.  
  
#### <a name="factors"></a>Factores  
 Para determinar qué tipo de indicador es adecuado, debe determinar los factores siguientes.  
  
1.  **Control de tiempo:** período de tiempo que tardará la operación  
  
2.  **Modalidad:** si la operación es modal en el entorno (bloqueos de la interfaz de usuario hasta que se complete el proceso)  
  
3.  **Persistent/transitorio:** si el resultado final del progreso debe ser notificado o visible en un momento posterior  
  
4.  **Determinado o indeterminado:** si se pueden calcular la hora de finalización de la operación y el progreso  
  
5.  **Ubicación del gráfico o Textual:** si el progreso o el proceso está capturado en línea, en el cuerpo de un mensaje o un control específico, como el control de árbol  
  
6.  **Proximidad:** si debe cerca de la interfaz de usuario que está relacionada con el progreso. ¿(Por ejemplo, puede estar en la barra de estado, que puede ser muy lejos, o deben ser junto al botón que inicia el proceso)?  
  
#### <a name="determinate-progress"></a>Progreso determinada  
  
|Tipo de progreso|Cuándo y cómo se utiliza|Notas|  
|-------------------|-------------------------|-----------|  
|Barra de progreso (determinado)|Se esperaba que dure > 5 segundos.<br /><br /> Puede incluir una descripción textual de detalles del proceso.|**No** insertar texto en la animación.|  
|Barra de información|Mensajería asociado a la interfaz de usuario contextual. Vea [barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Puede incluir una descripción textual de detalles del proceso.|**No** usa varias barras de información cuando se necesita indicar varios procesos. Utilice las barras de progreso apiladas en su lugar.|  
|Resultados (Ventana)|Notificación transitorio: proceso de nivel de aplicación que desea que el usuario **revisar** detalles de una vez finalizada.|**No** usar si el usuario deberá hacer referencia a los datos más adelante.|  
|Archivo de registro|Emparejado con intransient notificación en los casos, cuando es importante **guardar** detalles después de completarse.||  
|Barra de estado|Notificación transitorio: proceso de nivel de aplicación que el usuario hará **no necesita** detalles de una vez finalizada.<br /><br /> Incluye una barra de progreso incrustado.<br /><br /> Puede incluir una descripción textual de detalles del proceso.||  
  
#### <a name="indeterminate-progress"></a>Progreso indeterminada  
  
|Tipo de progreso|Cuándo y cómo se utiliza|Notas|  
|-------------------|-------------------------|-----------|  
|Barra de progreso (indeterminado)|Se esperaba que dure > 5 segundos.<br /><br /> Puede incluir una descripción textual de detalles del proceso.|**No** insertar texto en la animación.|  
|Hormigas (animados puntos horizontales)|Ida y vuelta al servidor.<br /><br /> Coloca el punto cercano de contexto a través de la parte superior del contenedor primario.|**No** use si no tienen elementos primarios por contenedor completo.|  
|Spinner (anillo de progreso)|Proceso asociado con la interfaz de usuario contextual o donde el espacio es una consideración.<br /><br /> Puede incluir una descripción textual de detalles del proceso.||  
|Barra de información|Mensajería asociado a la interfaz de usuario contextual. Vea [barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**No** usa varias barras de información cuando se necesita indicar varios procesos. Utilice las barras de progreso apiladas en su lugar.|  
|Resultados (Ventana)|Notificación transitorio: proceso de nivel de aplicación que el usuario desee **revisar** detalles de una vez finalizada.|**No** usar para la información que necesita para persisten en todas las sesiones.|  
|Archivo de registro|Emparejado con intransient notificación en los casos, cuando es importante **guardar** detalles después de completarse.||  
|Barra de estado|Notificación transitorio: proceso de nivel de aplicación que el usuario hará **no necesita** detalles de una vez finalizada.<br /><br /> Incluye la barra de progreso incrustado.<br /><br /> Puede incluir una descripción textual de detalles del proceso.||  
  
### <a name="progress-indicator-types"></a>Tipos de indicador de progreso  
  
#### <a name="progress-bars"></a>Barras de progreso  
  
##### <a name="indeterminate"></a>Indeterminado  
 ![Barra de progreso indeterminada](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "04_Indeterminate 0901")  
  
 **Barra de progreso indeterminada**  
  
 "Indeterminado" significa que todo el progreso de una operación o no se puede determinar el proceso. Utilice las barras de progreso indeterminada para las operaciones que requieren una cantidad ilimitada de tiempo o que tienen acceso a un número desconocido de objetos. Use una descripción textual para acompañar a lo que está sucediendo. Utilizar tiempos de espera para dar a los límites para operaciones basadas en tiempo. Barras de progreso indeterminada utilice animaciones para mostrar que progreso se está realizando, pero no proporcionar ninguna otra información. No elija una barra de progreso indeterminada basándose únicamente en la posible falta de precisión por sí sola.  
  
##### <a name="determinate"></a>Determinada  
 ![Barra de progreso determinada](../../extensibility/ux-guidelines/media/0901-05_determinate.png "05_Determinate 0901")  
  
 **Barra de progreso determinada**  
  
 "Determinado" significa que una operación o un proceso requiere una cantidad limitada de tiempo, incluso si esa cantidad de tiempo no se puede predecir con precisión. Indicar claramente la finalización. No permita que una barra de progreso vaya al 100 por ciento, a menos que se complete la operación. Animación de la barra de progreso determinada mueve izquierda a derecha de 0 a 100%.  
  
 Nunca se mueven el indicador de progreso con versiones anteriores durante una operación. La barra debe avanzar constantemente cuando comience la operación y llegar a 100% cuando termina. El punto de la barra de progreso consiste en que al usuario haga una idea de cuánto tarda de toda la operación, independientemente de cuántos pasos implicados.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Simultánea reporting (barras de progreso apiladas)  
 Si una operación tarda mucho tiempo - quizás se pueden usar varios minutos -, a continuación, barras de progreso de dos, uno que muestra el progreso general para una operación y otra para la progresión del paso actual. Por ejemplo, si un programa de instalación está copiando todos los archivos, puede utilizar una barra de progreso para indicar cuánto tiempo todo el proceso tarda un segundo puede indicar qué porcentaje del archivo actual o el directorio que se va a copiar. No informan de más de cinco procesos con barras de progreso apiladas o las operaciones simultáneas. Si tiene más de cinco operaciones simultáneas o procesos para informes, utilice un cuadro de diálogo modal con un botón de cancelación y el informe los detalles de progreso en la ventana de salida.  
  
##### <a name="textual-descriptions"></a>Descripciones textuales  
 Use una descripción textual que acompañan a lo que está sucediendo y el tiempo estimado para la finalización. Si no es posible determinar cuánto tardará una operación, podría ser una mejor opción para enviar comentarios de un icono animado en lugar de una barra de progreso.  
  
 Visual Studio proporciona una barra de progreso estándar en la barra de estado que puede usarse en cualquier producto integrada en Visual Studio. Para obtener una descripción textual de lo que sucede mientras la barra de progreso está animada, se puede actualizar el texto de la barra de estado.  
  
#### <a name="other-progress-indicators"></a>Otros indicadores de progreso  
  
##### <a name="ants-animated-horizontal-dots"></a>Hormigas (animados puntos horizontales)  
 ![Hormigas de progreso](../../extensibility/ux-guidelines/media/0903-01_ants.png "01_Ants 0903")  
  
 "Las hormigas," animados puntos horizontales, ofrecen una referencia visual para un proceso de servidor de ida y vuelta indeterminado.  
  
##### <a name="spinner-progress-ring"></a>Spinner (anillo de progreso)  
 ![Control giratorio de progreso](../../extensibility/ux-guidelines/media/0903-02_spinner.png "02_Spinner 0903")  
  
 El control de número (también conocido como un "anillo de progreso") es un indicador de progreso indeterminada que se utiliza principalmente en relación con la interfaz de usuario contextual. Mostrar un control de número cerca de su contenido relacionado, como un encabezado de categoría textual, mensajería o control.  
  
##### <a name="cursor-feedback"></a>Información del cursor  
 Para las operaciones que tarden entre 2 a 7 segundos, proporcione la información del cursor. Normalmente, esto significa que con el cursor de espera proporcionado por el sistema operativo. Para obtener instrucciones, consulte el artículo de MSDN [Cursors.Wait propiedad](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx).  
  
#### <a name="progress-indicator-locations"></a>Ubicaciones de indicador de progreso  
  
##### <a name="status-bar"></a>Barra de estado  
 La barra de estado proporciona un lugar donde se muestran mensajes e información útil al usuario sin interrumpir el trabajo del usuario de la aplicación. Normalmente se muestra en la parte inferior de una ventana, estado de progreso será un panel de información sobre herramientas que incluye un mensaje acerca de la medida del progreso en combinación con un indicador de la barra de progreso.  
  
 ![Barra de estado con barra de progreso](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "03_StatusBarProgressBar 0903")  
  
 **Barra de estado con barra de progreso**  
  
 ![Barra de estado con mensajería](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "04_StatusBarMessage 0903")  
  
 **Barra de estado con texto descriptivo**  
  
##### <a name="infobar"></a>Barra de información  
 Similar a la barra de estado, la barra de información proporciona notificación contextual y los mensajes, que también se pueden emparejar con indicadores de progreso indeterminada, como la barra de progreso o el control de giro. La barra de información no debería proporcionar progreso nivel granular o indicación de progreso determinada. Vea [barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Barra de información con barra de progreso y mensajería](../../extensibility/ux-guidelines/media/0903-05_infobar.png "05_InfoBar 0903")  
  
 **Barra de información con barra de progreso y la descripción textual**  
  
 ![Barra de información dentro de una ventana](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "06_InfoBarInWindow 0903")  
  
 **Barra de información dentro de la ventana de análisis de código**  
  
##### <a name="inline"></a>Alineado  
 Indicación de progreso en línea puede representarse mediante cualquiera de los tipos de cargador de progreso. Normalmente el indicador de progreso se empareja con mensajería, pero esto no es un requisito.  
  
 ![Control giratorio de progreso en línea](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "07_InlineSpinner 0903")  
  
 **Combinada con la descripción textual del control de giro**  
  
 ![Barras de progreso de apiladas en línea](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "08_InlineStackedProgress 0903")  
  
 **Barras de progreso apiladas determinada**  
  
 ![Mensajes de progreso en línea](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "09_InlineText 0903")  
  
 **Texto insertado de explorador de servidor: actualizar...**  
  
##### <a name="tool-windows"></a>Ventanas de herramientas  
 Indicación de progreso global está representado por una barra de progreso indeterminada colocada directamente debajo de la barra de herramientas.  
  
 ![Barra de progreso indeterminada global](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "23_GlobalIndeterminate 0903")  
  
 **Barra de progreso indeterminada global de Team Explorer**  
  
##### <a name="dialogs"></a>Cuadros de diálogo  
 Los cuadros de diálogo pueden contener cualquiera de los tipos de cargador de progreso. Indicadores de progreso pueden ser emparejados con mensajería así como combinar con varios niveles de indicación de progreso para representar granular y procesos de sub.  
  
 ![Cuadro de diálogo con varios tipos de indicador de progreso](../../extensibility/ux-guidelines/media/0903-11_dialog.png "11_Dialog 0903")  
  
 **Cuadro de diálogo de Visual Studio con procesos simultáneos y varios tipos de indicador de progreso**  
  
 ![Cuadro de diálogo con cargador de progreso y mensajería](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "12_Dialog2 0903")  
  
 **Cuadro de diálogo de Visual Studio con cargador de progreso y mensajes en línea de comandos**  
  
##### <a name="document-well"></a>Cuadro de documento  
 El documento también puede mostrar varios tipos de cargador de progreso en combinación con los controles.  
  
 ![Mensajes de progreso en documento también](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "13_DocumentWell 0903")  
  
 **Barra de progreso indeterminada por debajo de la barra de herramientas**  
  
##### <a name="output-window"></a>Resultados (Ventana)  
 La ventana de salida es adecuada para controlar la progresión del proceso y el estado de progreso en curso a través de mensajería de texto insertado. Debe usar la barra de estado junto con los informes de progreso de ventana de salida.  
  
 ![Mensajes de progreso en la ventana de salida](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "14_OutputWindow 0903")  
  
 **Ventana de salida con el estado del proceso actual y esperar de mensajería**  
  
##  <a name="BKMK_Infobars"></a>Barras de información  
  
### <a name="overview"></a>Información general  
 Barras de información proporcionan al usuario un indicador cerca de su punto de atención y usando el control de barra de información compartida garantiza la coherencia de la apariencia visual y la interacción.  
  
 ![Barra de información](../../extensibility/ux-guidelines/media/0904-01_infobar.png "01_Infobar 0904")  
  
 **Barras de información en Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>El uso apropiado de una barra de información  
  
-   Para proporcionar al usuario un mensaje de no bloqueo pero importante pertinente para el contexto actual  
  
-   Para indicar que la interfaz de usuario está en un determinado estado o condición que no tiene algunas implicaciones de interacción, como la depuración histórica  
  
-   Para notificar al usuario que el sistema ha detectado problemas, como cuando una extensión está causando problemas de rendimiento  
  
-   Para permitir a los usuarios una manera de usar fácilmente la acción, por ejemplo, cuando el editor detecta que un archivo mezclan tabulaciones y espacios  
  
##### <a name="do"></a>Hacer:  
  
-   Mantenga el texto de mensaje de la barra de información cortas y en el punto.  
  
-   Mantenga el texto en los vínculos y botones concisa.  
  
-   Asegúrese de que las opciones de "acción" proporcionar a los usuarios son mínimas, que muestra sólo las acciones necesarias.  
  
##### <a name="dont"></a>No:  
  
-   Usar una barra de información para ofrecer comandos estándar que se deben colocar en una barra de herramientas.  
  
-   Usar una barra de información en lugar de un cuadro de diálogo modal.  
  
-   Cree un mensaje fuera de una ventana flotante.  
  
-   Utilice varias barras de información en varias ubicaciones dentro de la misma ventana.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>¿Pueden mostrar varias barras de información al mismo tiempo?  
 Sí, pueden mostrar varias barras de información al mismo tiempo. Se mostrará en orden de primero ENTRAR, primero en ser atendido con la primera barra de información que muestra en barras de información superior y adicional que se muestra a continuación.  
  
 El usuario verá un máximo de tres barras de información a la vez, después de que, si existen más barras de información, la región de la barra de información se convertirá en desplazable.  
  
### <a name="creating-an-infobar"></a>Crear una barra de información  
 La barra de información tiene cuatro secciones, de izquierda a derecha:  
  
-   **Icono:** aquí es donde se agrega cualquier icono que le gustaría mostrar de la barra de información, como un icono de advertencia.  
  
-   **Texto:** puede agregar texto que describa al usuario de escenario/situación es, junto con los vínculos en el texto, si es necesario. Recuerde que debe mantener el texto concisa.  
  
-   **Acciones:** en esta sección debe contener vínculos y botones de las acciones que el usuario puede llevar a cabo en la barra de información.  
  
-   **Botón Cerrar:** la última sección a la derecha puede tener un botón de cierre.  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>Crear una barra de información estándar en código administrado  
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
  
 Este es un ejemplo que crea un InfoBarModel algún texto con un hipervínculo, un botón de acción y un icono.  
  
 ![Barra de información con hipervínculo](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "02_InfobarHyperlink 0904")  
  
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
 Implementar una interfaz IVsInfoBar el fin de proporcionar una barra de información desde el código nativo.  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Obtener una barra de información UIElement de una barra de información  
 La implementación de InfoBarModel o IVsInfoBar son modelos de datos que se deben convertir en un elemento de IU para que se muestre en la interfaz de usuario. UIElement se puede recuperar con el servicio de SVsInfoBarUIFactory/IVsInfoBarUIFactory.  
  
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
 Barras de información se pueden mostrar en una o varias de las siguientes ubicaciones:  
  
-   Ventanas de herramientas  
  
-   Dentro de una pestaña de documento  
  
> [!IMPORTANT]
>  Es posible colocar una barra de información para proporcionar un mensaje acerca del contexto global. Debería aparecer entre las barras de herramientas y el cuadro de documento. No se recomienda porque hace que los problemas con "saltar y jerk" del IDE y debe evitarse, a menos que sea absolutamente necesario y apropiado.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Y se coloca una barra de información en un ToolWindowPane  
 El método ToolWindowPane.AddInfoBar(IVsInfoBar) puede usarse para agregar una barra de información a una ventana de herramientas. Esta API puede agregar una IVsInfoBar (de qué InfoBarModel es una implementación predeterminada), o un IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Y se coloca una barra de información en un documento o no ToolWindowPane  
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
  
#### <a name="placing-an-infobar-in-the-main-window"></a>Y se coloca una barra de información en la ventana principal  
 Para colocar una barra de información en la ventana principal, use la VSSPROPID_MainWindowInfoBarHost del servicio IVsShell para obtener IVsInfoBarHost de la ventana principal y, a continuación, agregue la barra de información UIElement.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>¿Se sabe cuando el usuario realice la acción en la barra de información?  
 Sí, cada acción de evento, se devolverá al autor de la barra de información. A continuación, es el autor de la barra de información para tomar medidas en el IDE en función de la selección del usuario en la barra de información. Barras de información se quitará automáticamente desde el host se ha hecho clic cuyo botón Cerrar, pero es necesario trabajo adicional si otra barras de información deba quitarse después de cerrar. Telemetría también tendrá que se registra de forma independiente para cada barra de información.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Recibir eventos de la barra de información en un ToolWindowPane  
 ToolWindowPane tiene dos eventos de barras de información. El evento InfoBarClosed se produce cuando se cierra una barra de información en el ToolWindowPane. El evento InfoBarActionItemClicked se desencadena cuando se hace clic en un hipervínculo o un botón en la barra de información.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Recepción de eventos de la barra de información directamente desde el UIElement  
 IVsInfoBarUIElement.Advise puede utilizarse para suscribirse a eventos directamente desde UIElement de una barra de información. Implementar IVsInfoBarUIEvents permitirá que el autor del cierre de recepción y haga clic en eventos.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a>Validación del error  
 Cuando un usuario escribe la información que no es aceptable, por ejemplo, cuando se omite un campo obligatorio o cuando se insertan datos en un formato incorrecto, es mejor para la validación de control de uso o comentarios cerca del control en lugar de usar un cuadro de diálogo de error emergente bloqueo.  
  
### <a name="field-validation"></a>Validación de campos  
 Validación del formulario y campo consta de tres componentes: un control, un icono y una información sobre herramientas. Aunque pueden usar varios tipos de controles de esto, un cuadro de texto se utilizará como un ejemplo.  
  
 ![Validación de campos &#40; espacio en blanco &#41; ] (../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "01_FieldValidation 0905")  
  
 Si el campo es obligatorio, debe haber texto que indica de marcas de agua  **\<necesario >** y el fondo del campo debe ser ligero amarillo (VSColor: `Environment.ControlEditRequiredBackground`) y el primer plano debería ser gris (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Campo de validación con la etiqueta "Obligatorio"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "02_FieldValidationRequired 0905")  
  
 El programa puede determinar que el control está en un estado de *contenido no válido especificado* cuando se mueve el foco a otro control o cuando el usuario hace clic en un botón [Aceptar] del confirmación o cuando el usuario guarda el documento o formulario.  
  
 Cuando se determina el estado de contenido no válido, aparece un icono dentro del control o justo detrás de él. Información sobre herramientas que describe el error debe aparecer al mantener el mouse del icono o el control. Además, debe aparecer un borde de 1 píxel alrededor del control que está creando el estado no válido.  
  
 ![Especificaciones de diseño de validación de campo](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "03_LayoutSpecs 0905")  
  
 **Especificaciones de diseño para la validación de campo**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Variaciones aceptables para la ubicación del icono  
 Hay muchas casos particulares en los que los usuarios necesitan estar informado acerca de los errores de validación. Teniendo en cuenta el tipo de control y la configuración de la interfaz de usuario, elija la ubicación del icono adecuada para su situación.  
  
 ![Ubicaciones aceptables para la ubicación del icono](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "04_IconLocation 0905")  
  
 **Variaciones aceptables para las ubicaciones de icono de validación de campo**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Necesidad de ida y vuelta a una conexión de red o de servidor de validación  
 En algunos casos, es necesario un ida y vuelta al servidor para comprobar el contenido y sería importante mostrar el progreso de usuario, comprobado y los Estados de error. La ilustración siguiente se muestra un ejemplo de este caso y la interfaz de usuario recomendada.  
  
 ![Validación que implica un recorrido de ida y a un servidor](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "05_RoundTrip 0905")  
  
 **Validación que implica un recorrido de ida y a un servidor**  
  
 Tenga en cuenta que se debe proporcionar suficiente espacio disponible a la derecha del control con el fin de dar cabida al texto "Comprobar..." y "Reintentar".  
  
#### <a name="in-place-warning-text"></a>Texto de la advertencia en contexto  
 Cuando hay espacio disponible para colocar el mensaje de error cerca del control en un estado de error, esto es preferible al uso de la información sobre herramientas independiente.  
  
 ![En &#45; lugar advertencia](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "06_InPlaceWarning 0905")  
  
 **Texto de la advertencia en contexto**  
  
#### <a name="watermarks"></a>Marcas de agua  
 A veces un control completo o la ventana está en un estado de error. En esta situación, utilice una marca de agua para indicar el error.  
  
 ![Marca de agua](../../extensibility/ux-guidelines/media/0905-07_watermark.png "07_Watermark 0905")  
  
 **Validación de campos de marca de agua**