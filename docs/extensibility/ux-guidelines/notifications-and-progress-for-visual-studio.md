---
title: Notificaciones y progreso de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f6a7ddd5d1a5a7257617b03098722e1341017b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699880"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Notificaciones y progreso para Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Sistemas de notificación

### <a name="overview"></a>Información general
 Hay varias maneras de informar al usuario de lo que ocurre en Visual Studio con respecto a sus tareas de desarrollo de software.

 Al implementar cualquier tipo de notificación:

- **Mantenga el número de notificaciones al** número efectivo mínimo. Los mensajes de notificación deben aplicarse a la mayoría de los usuarios de Visual Studio o a los usuarios de un área específica de características o características. Un uso excesivo de las notificaciones puede SideTrack al usuario o reducir la facilidad de uso del sistema.

- **Asegúrese de que está presentando mensajes claros y accionables** que el usuario puede usar para invocar el contexto adecuado con el fin de tomar decisiones más complejas y tomar medidas adicionales.

- **Presente mensajes sincrónicos y asincrónicos correctamente.** Las notificaciones sincrónicas indican que algo requiere atención inmediata, como cuando un servicio Web se bloquea o se produce una excepción de código. Se debe informar al usuario de esas situaciones de forma inmediata de una manera que requiera su entrada, como en un cuadro de diálogo modal. Las notificaciones asincrónicas son aquellas que el usuario debe conocer pero que no deben actuar de inmediato, como cuando se completa una operación de compilación o cuando finaliza la implementación de un sitio Web. Esos mensajes deben ser más ambientales y no interrumpir el flujo de tareas del usuario.

- **Utilice los cuadros de diálogo modales solo cuando sea necesario para evitar que el usuario realice otras acciones antes de** confirmar el mensaje o tomar una decisión presentada en el cuadro de diálogo.

- **Quite las notificaciones ambientales cuando ya no sean válidas.** No es necesario que el usuario descarte una notificación si ya ha tomado medidas para solucionar el problema del que se ha notificado.

- **Tenga en cuenta que las notificaciones pueden provocar correlaciones falsas.** Los usuarios pueden creer que una o varias de sus acciones han desencadenado una notificación cuando de hecho no había ninguna relación causal. Esté claro en el mensaje de notificación sobre el contexto, el desencadenador y el origen de la notificación.

### <a name="choosing-the-right-method"></a>Elección del método Right
 Use esta tabla para ayudarle a elegir el método correcto para notificar al usuario sobre el mensaje.

|Método|Usar|No debe usarse|
|------------|---------|----------------|
|[Cuadros de diálogo de mensajes de error modales](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Use cuando sea necesaria una respuesta de usuario antes de continuar.|No se usa cuando no es necesario bloquear al usuario e interrumpir el flujo. Evite el uso de cuadros de diálogo modales si es posible mostrar el mensaje de otro modo menos intrusivo.|
|[Barra de estado de IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Use cuando haya información de texto ambiente relativa al estado de un proceso.|No utilice solo. Se utiliza mejor junto con otro mecanismo de comentarios.|
|[Barra de información incrustada](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|En una ventana de herramientas o una ventana de documento, utilice para notificar el progreso, el estado del error, los resultados o la información procesable.|No use si la información no es relevante para la ubicación donde se coloca la barra de información.<br /><br /> No use fuera de una ventana de documento o de herramientas.|
|[Cambios del cursor del mouse](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Se puede usar para notificar que un proceso está en curso. También se utiliza para notificar que hay un cambio de estado en el mouse, por ejemplo, cuando la acción de arrastrar y colocar está en curso o si el cursor del mouse está en un modo determinado, como el modo de dibujo.|No se usa para los cambios de progreso breves o si es probable que Fluttering del cursor (por ejemplo, cuando se enlaza a partes de un proceso de ejecución más larga en lugar de a todo el proceso).|
|[Indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Use cuando necesite informar del progreso (determine o indeterminado). Hay una variedad de tipos de indicadores de progreso y el uso específico de cada uno. Vea [indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Ventana de notificaciones de Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La ventana notificaciones no es extensible públicamente. Sin embargo, se usa para comunicar una variedad de mensajes sobre Visual Studio, incluidos los problemas críticos con la licencia y las notificaciones informativas de las actualizaciones de Visual Studio o de los paquetes.|No use para otros tipos de notificaciones.|
|[Lista de errores](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Cuando el problema se relaciona directamente con la solución abierta actualmente del usuario con un problema (error, ADVERTENCIA o información), es posible que tenga que tomar medidas en el código.<br /><br /> Esto incluye, por ejemplo:<br /><br /> -Mensajes del compilador (error, ADVERTENCIA o información)<br /><br /> -Analizador de código/mensajes de diagnóstico sobre el código<br /><br /> -Mensajes de compilación<br /><br /> Puede ser adecuado para los problemas relacionados con los archivos de proyecto o solución, pero tenga en cuenta una indicación Explorador de soluciones en primer lugar.|No se usa para los elementos que no tienen ninguna relación con el código de la solución abierta del usuario.|
|Notificaciones del editor: bombilla|Use cuando tenga una solución disponible para solucionar un problema que exista en el archivo abierto.<br /><br /> Tenga en cuenta que la bombilla también debe usarse para hospedar acciones rápidas que se tomen en el código de usuario a petición, como refactorizaciones, pero en ese caso no aparecerá "estilo de notificación".|No se usa para los elementos que no tienen ninguna relación con el archivo abierto.|
|Notificaciones del editor: garabatos|Use para avisar al usuario de un problema con un intervalo determinado de su código abierto (por ejemplo, un subrayado ondulado de color rojo para errores).|No se usa para los elementos que no están relacionados con un intervalo determinado de su código abierto.|
|[Barras de estado incrustadas](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Se usa para proporcionar el estado relacionado con el contenido o el proceso en el contexto de una ventana de herramientas, una ventana de documento o una ventana de diálogo concretos.|No se usa para las notificaciones de producto generales, los procesos o los elementos que no tienen ninguna relación con el contenido de la ventana específica.|
|[Notificaciones de la bandeja de Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Se usa para exponer notificaciones para procesos fuera de proceso o aplicaciones complementarias.|No se usa para las notificaciones que son relevantes para el IDE.|
|[Burbujas de notificación](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Se usa para notificar a un proceso remoto o cambiar **fuera** del IDE.|No utilice como medio para notificar al usuario los procesos **dentro** del IDE.|

### <a name="notification-methods"></a>Métodos de notificación

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Cuadros de diálogo de mensajes de error modales
 Se usa un cuadro de diálogo de mensaje de error modal para mostrar un mensaje de error que requiere la confirmación o la acción del usuario.

 ![Mensaje de error modal](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Cuadro de diálogo de mensaje de error modal que alerta al usuario de una cadena de conexión no válida a una base de datos**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> Barra de estado de IDE
 La probabilidad de que los usuarios observen que el texto de la barra de estado se correlaciona con la experiencia del equipo y la experiencia específica con la plataforma Windows. La base de clientes de Visual Studio tiende a tener experiencia en ambas áreas, aunque los usuarios de Windows con conocimiento podrían omitir los cambios en la barra de estado. Por lo tanto, la barra de estado se utiliza con fines informativos o como una indicación redundante para la información que se presenta en otro lugar. Cualquier tipo de información crítica que el usuario deba resolver inmediatamente debe proporcionarse en un cuadro de diálogo o en la ventana de herramientas de notificaciones.

 La barra de estado de Visual Studio está diseñada para permitir que se muestren varios tipos de información. Se divide en regiones para los comentarios, el diseñador, la barra de progreso, la animación y el cliente.

 La región de comentarios y la región del diseñador siempre están visibles. La barra de progreso y las regiones de animación siempre son dinámicas y se basan en el contexto del usuario. La región del diseñador tiene un ancho estático determinado por la longitud de la cadena que se extrae de un recurso adjunto para el mensaje de texto. Esto permite a la localización cambiar el tamaño del ancho sin necesidad de un cambio de código. En inglés, el ancho de esta cadena es de aproximadamente 220 píxeles. La región del diseñador se comportará de la forma habitual y la región de comentarios absorberá el espacio restante.

 La barra de estado también está coloreada para agregar interés visual y valor funcional mediante la comunicación de varios cambios de estado del IDE, como cuando el IDE está en modo de depuración.

 ![Cambios de color de la barra de estado IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Colores de la barra de estado del IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Barra de barra incrustada
 Se puede usar una barra de información en la parte superior de una ventana de documento o una ventana de herramientas para informar al usuario de un estado o una condición. También puede ofrecer comandos para que el usuario pueda tener una manera fácil de tomar medidas. La barra de barra es un control de Shell estándar. Evite crear el suyo propio, que actuará y aparecerá incoherente con otros en el IDE. Consulte [las barras](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) para obtener detalles de implementación e instrucciones de uso.

 ![Barra de información incrustada](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Barra de información incrustada en una ventana de documento, que avisa al usuario de que el IDE está en modo de depuración histórica y el editor no responde de la misma manera que en el modo de depuración estándar.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Cambios del cursor del mouse
 Al cambiar el cursor del mouse, use los colores que están vinculados al servicio VSColor y que ya están asociados al cursor. Los cambios de cursor se pueden usar para indicar una operación en curso, así como las zonas de posicionamiento en las que el usuario mantiene el mouse sobre un destino que se puede arrastrar, colocar en o utilizar para seleccionar un objeto.

 Use el cursor del mouse ocupado/wait solo cuando todo el tiempo de CPU disponible debe estar reservado para una operación, evitando que el usuario exprese cualquier entrada adicional. En la mayoría de los casos, con aplicaciones bien escritas que usan multithreading, los momentos en los que se impide que los usuarios realicen otras operaciones no deben ser raros.

 Tenga en cuenta que los cambios de cursor son útiles como una indicación redundante para la información que se presenta en otro lugar. No confíe en un cambio de cursor como la única forma de comunicarse con el usuario, especialmente cuando intenta transmitir algo que es fundamental que el usuario debe resolver.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Indicadores de progreso
 Los indicadores de progreso son importantes para proporcionar los comentarios de los usuarios durante los procesos que tardan más de unos segundos en completarse. Los indicadores de progreso se pueden mostrar en contexto (cerca del punto de inicio de la acción en curso), en una barra de estado incrustada, en un cuadro de diálogo modal o en la barra de estado de Visual Studio. Siga las instrucciones de los [indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) con respecto a su uso e implementación.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Ventana de notificaciones de Visual Studio
 La ventana de notificaciones de Visual Studio informa a los desarrolladores sobre las licencias, el entorno (Visual Studio), las extensiones y las actualizaciones. Los usuarios pueden descartar las notificaciones individuales o pueden optar por omitir determinados tipos de notificaciones. La lista de notificaciones omitidas se administra en una página de **herramientas > opciones** .

 La ventana notificaciones no es extensible actualmente.

 ![Ventana de notificaciones de Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Ventana de herramientas de notificaciones de Visual Studio**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Lista de errores
 Una notificación dentro de la lista de errores indica errores y advertencias que se produjeron durante la compilación o el proceso de compilación, y permite al usuario navegar por el código a ese error de código concreto.

 ![Lista de errores](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Lista de errores en Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Barras de estado incrustadas
 Dado que la barra de estado del IDE es dinámica, con su contexto de región de cliente establecido en la ventana de documento activa y la actualización de información en el contexto del usuario o en las respuestas del sistema, es difícil mantener una visualización continua de la información o dar el estado a los procesos asincrónicos a largo plazo. Por ejemplo, la barra de estado del IDE no es adecuada para las notificaciones de los resultados de la serie de pruebas para varias ejecuciones o selecciones de elementos que se puedan realizar de forma inmediata. Es importante conservar dicha información de estado en el contexto del documento o de la ventana de herramientas, donde el usuario realiza una selección o inicia un proceso.

 ![Barra de estado incrustada](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Barra de estado incrustada en Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Notificaciones de la bandeja de Windows
 El área de notificación de Windows se encuentra junto al reloj del sistema en la barra de tareas de Windows. Muchas utilidades y componentes de software proporcionan iconos en esta área para que el usuario pueda obtener un menú contextual para tareas en todo el sistema, como cambiar la resolución de la pantalla u obtener actualizaciones de software.

 Las notificaciones de nivel de entorno deben aparecer en el centro de notificaciones de Visual Studio, no en el área de notificación de Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Burbujas de notificación
 Las burbujas de notificación pueden aparecer como información en un editor o diseñador, o como parte del área de notificación de Windows. El usuario percibe estas burbujas como problemas que pueden resolver más adelante, lo que supone una ventaja para las notificaciones no críticas. Las burbujas no son adecuadas para la información crítica que el usuario debe resolver de inmediato. Si usa burbujas de notificación en Visual Studio, siga las [instrucciones del escritorio de Windows para las burbujas de notificación](/windows/desktop/uxguide/mess-notif).

 ![Burbuja de notificación](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Burbuja de notificación en el área de notificación de Windows usada para Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Indicadores de progreso

### <a name="overview"></a>Información general
 Los indicadores de progreso son una parte importante de un sistema de notificación para proporcionar los comentarios de los usuarios. Indican al usuario Cuándo se completarán los procesos y las operaciones. Los tipos de indicadores familiares incluyen barras de progreso, cursores hilados e iconos animados. El tipo y la ubicación de un indicador de progreso depende del contexto, incluidos los informes y el tiempo que tardará en completarse el proceso u operación.

#### <a name="factors"></a>Factores
 Para determinar qué tipo de indicador es adecuado, debe determinar los siguientes factores.

1. **Timing:** cantidad de tiempo que tardará la operación

2. **Modalidad:** si la operación es modal para el entorno (bloquea la interfaz de usuario hasta que se complete el proceso)

3. **Persistente/transitorio:** si el resultado final del progreso debe aparecer o informarse en un momento posterior

4. **Determinate/indeterminado:** si se puede calcular la hora de finalización y el progreso de la operación

5. **Ubicación de gráfico/textual:** si el progreso o el proceso se capturan en línea, en el cuerpo de un mensaje o en un control concreto, como el control de árbol

6. **Proximidad:** si el progreso debe estar cerca de la interfaz de usuario con la que está relacionado. (Por ejemplo, puede estar en la barra de estado, que puede estar lejos o debe estar cerca del botón que inició el proceso?)

#### <a name="determinate-progress"></a>Finalizar el progreso

|Tipo de progreso|Cuándo y cómo usar|Notas|
|-------------------|-------------------------|-----------|
|Barra de progreso (desterminar)|Duración esperada de >5 segundos.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**No** Inserte texto en la animación.|
|Barra de información|Mensajería asociada a la interfaz de usuario contextual. Vea [las barras](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**No** use varios las barras cuando necesite indicar varios procesos. En su lugar, use barras de progreso apiladas.|
|Ventana de salida|Notificación transitoria: proceso de nivel de aplicación en el que el usuario desea **revisar** los detalles después de la finalización.|**No** utilice si el usuario deberá hacer referencia a los datos más adelante.|
|Archivo de registro|Emparejado con notificación intransitoria en casos en los que es importante **Guardar** los detalles después de la finalización.||
|Barra de estado|Notificación transitoria: proceso de nivel de aplicación para el que el usuario **no necesitará** detalles después de la finalización.<br /><br /> Incluye una barra de progreso incrustada.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||

#### <a name="indeterminate-progress"></a>Progreso indeterminado

|Tipo de progreso|Cuándo y cómo usar|Notas|
|-------------------|-------------------------|-----------|
|Barra de progreso (indeterminada)|Duración esperada de >5 segundos.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**No** Inserte texto en la animación.|
|Hormigas (puntos horizontales animados)|Ida y vuelta al servidor.<br /><br /> Se coloca cerca del punto de contexto a lo largo de la parte superior del contenedor principal.|**No** utilice si no es un elemento primario de un contenedor completo.|
|Control de número (anillo de progreso)|Proceso asociado a la interfaz de usuario contextual o donde el espacio es una consideración.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||
|Barra de información|Mensajería asociada a la interfaz de usuario contextual. Vea [las barras](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**No** use varios las barras cuando necesite indicar varios procesos. En su lugar, use barras de progreso apiladas.|
|Ventana de salida|Notificación transitoria: proceso de nivel de aplicación que el usuario querrá **revisar** los detalles de la finalización.|**No** use para la información que debe persistir entre sesiones.|
|Archivo de registro|Emparejado con notificación intransitoria en casos en los que es importante **Guardar** los detalles después de la finalización.||
|Barra de estado|Notificación transitoria: proceso de nivel de aplicación para el que el usuario **no necesitará** detalles después de la finalización.<br /><br /> Incluye una barra de progreso incrustada.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||

### <a name="progress-indicator-types"></a>Tipos de indicadores de progreso

#### <a name="progress-bars"></a>Barras de progreso

##### <a name="indeterminate"></a>Determina
 ![Barra de progreso indeterminado](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Barra de progreso indeterminado**

 "Indeterminado" significa que no se puede determinar el progreso general de una operación o proceso. Use barras de progreso indeterminadas para las operaciones que requieren un período de tiempo ilimitado o que tengan acceso a un número desconocido de objetos. Use una descripción textual para acompañar lo que está ocurriendo. Utilice los tiempos de espera para proporcionar límites a las operaciones basadas en el tiempo. Las barras de progreso indeterminadas usan animaciones para mostrar que se está realizando el progreso, pero no proporcionan ninguna otra información. No elija una barra de progreso indeterminada basada únicamente en la falta de precisión.

##### <a name="determinate"></a>Determinada
 ![Barra de progreso determinada](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Barra de progreso determinada**

 "Determinate" significa que una operación o proceso requiere una cantidad limitada de tiempo, incluso si esa cantidad de tiempo no se puede predecir con precisión. Indique claramente la finalización. No permita que una barra de progreso vaya al 100 por ciento, a menos que la operación se haya completado. La animación de la barra de progreso de determinaciones se mueve de izquierda a derecha de 0 a 100%.

 Nunca mueva el indicador de progreso hacia atrás durante una operación. La barra debe avanzar de vez en cuando se inicia la operación y alcanzar el 100% cuando termina. El punto de la barra de progreso es ofrecer al usuario una idea de cuánto tiempo tarda la operación completa, independientemente del número de pasos que intervengan.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Informes simultáneos (barras de progreso apiladas)
 Si una operación tardará mucho tiempo (quizás varios minutos), se pueden usar dos barras de progreso, una que muestra el progreso general de una operación y otra para la progresión del paso actual. Por ejemplo, si un programa de instalación está copiando muchos archivos, se puede usar una barra de progreso para indicar cuánto tiempo tarda el proceso completo mientras que un segundo puede indicar qué porcentaje del archivo o directorio actual se está copiando. No informe de más de cinco operaciones o procesos simultáneos mediante barras de progreso apiladas. Si tiene más de cinco operaciones o procesos simultáneos que se van a notificar, use un cuadro de diálogo modal con un botón Cancelar e informe de los detalles del progreso en el Ventana de salida.

##### <a name="textual-descriptions"></a>Descripciones textuales
 Use una descripción textual para acompañar lo que está ocurriendo y el tiempo estimado para la finalización. Si no es posible determinar cuánto tiempo tardará una operación, una opción mejor para proporcionar comentarios podría ser un Icono animado en lugar de una barra de progreso.

 Visual Studio proporciona una barra de progreso estándar en la barra de estado que puede usar cualquier producto integrado en Visual Studio. Para obtener descripciones textuales de lo que está ocurriendo mientras se anima la barra de progreso, se puede actualizar el texto de la barra de estado.

#### <a name="other-progress-indicators"></a>Otros indicadores de progreso

##### <a name="ants-animated-horizontal-dots"></a>Hormigas (puntos horizontales animados)
 ![Hormigas de progreso](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Hormigas", "puntos horizontales animados, proporcionan una referencia visual para un proceso de servidor de ida y vuelta indeterminado.

##### <a name="spinner-progress-ring"></a>Control de número (anillo de progreso)
 ![Control giratorio de progreso](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 El control de número (también conocido como "anillo de progreso") es un indicador de progreso indeterminado que se usa principalmente en relación con la interfaz de usuario contextual. Mostrar un control de número cerca de su contenido relacionado, como un encabezado de categoría textual, la mensajería o el control.

##### <a name="cursor-feedback"></a>Comentarios del cursor
 Para las operaciones que tardan entre 2-7 segundos, proporcione comentarios sobre el cursor. Normalmente, esto significa usar el cursor de espera proporcionado por el sistema operativo. Para obtener instrucciones, consulte la [propiedad cursores. Wait](/dotnet/api/system.windows.input.cursors.wait)de MSDN article.

#### <a name="progress-indicator-locations"></a>Ubicaciones del indicador de progreso

##### <a name="status-bar"></a>Barra de estado
 La barra de estado proporciona a la aplicación un lugar para mostrar mensajes e información útil al usuario sin interrumpir el trabajo del usuario. Normalmente, en la parte inferior de una ventana, el estado de progreso será un panel de información sobre herramientas que incluye un mensaje sobre la medida de progreso en combinación con un indicador de barra de progreso.

 ![Barra de estado con barra de progreso](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Barra de estado con barra de progreso**

 ![Barra de estado con mensajes](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Barra de estado con descripción textual**

##### <a name="infobar"></a>Barra de información
 De forma similar a la barra de estado, la barra de información proporciona notificación y mensajería contextuales, que también se pueden emparejar con indicadores de progreso indeterminados, como la barra de progreso o el control de número. La barra de información no debe proporcionar una indicación de progreso de nivel granular o de desterminación. Vea [las barras](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Barra de información con barra y mensajes de progreso](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Barra de estado con barra de progreso y descripción textual**

 ![Barra de información dentro de una ventana](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>En línea
 La indicación de progreso en línea se puede representar con cualquiera de los tipos de cargador de progreso. Normalmente, el indicador de progreso se empareja con la mensajería, pero no es un requisito.

 ![Control giratorio de progreso en línea](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Control de número combinado con descripción textual**

 ![Barras de progreso apiladas en línea](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Desterminación de barras de progreso apiladas**

 ![Mensajes de progreso en línea](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Explorador de servidores texto insertado: actualizando...**

##### <a name="tool-windows"></a>Ventanas de herramientas
 La indicación de progreso global se representa mediante una barra de progreso indeterminada situada directamente debajo de la barra de herramientas.

 ![Barra de progreso indeterminada global](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer barra de progreso indeterminada global**

##### <a name="dialogs"></a>Cuadros de diálogo
 Los cuadros de diálogo pueden contener cualquiera de los tipos de cargador de progreso. Los indicadores de progreso se pueden emparejar con la mensajería y combinarse con varios niveles de indicación de progreso para representar la granularidad y los subprocesos.

 ![Cuadro de diálogo con varios tipos de indicador de progreso](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Cuadro de diálogo de Visual Studio con procesos simultáneos y varios tipos de indicadores de progreso**

 ![Cuadro de diálogo con cargador y mensajes de progreso](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Cuadro de diálogo de Visual Studio con el cargador de progreso y comandos insertados de mensajería**

##### <a name="document-well"></a>Cuadro de documento
 El cuadro de documento puede mostrar varios tipos de cargador de progreso en combinación con los controles.

 ![Mensajes de progreso en la sección de documentos](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Barra de progreso indeterminada debajo de la barra de herramientas**

##### <a name="output-window"></a>Ventana de salida
 La ventana de salida es adecuada para controlar la progresión de procesos y el estado de progreso en curso a través de la mensajería de texto en línea. Debe usar la barra de Estado junto con los informes de progreso de la ventana de salida.

 ![Mensajes de progreso en la ventana de salida](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Ventana de salida con el estado de proceso continuo y la mensajería de espera**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Las barras

### <a name="overview"></a>Información general
 Las barras al usuario un indicador cercano a su punto de atención y el uso del control de barra de información compartido garantiza la coherencia en el aspecto visual y la interacción.

 ![Barra de información](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Las barras en Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Usos adecuados para una barra de información

- Para proporcionar al usuario un mensaje que no sea de bloqueo pero importante relevante para el contexto actual

- Para indicar que la interfaz de usuario está en un estado determinado o una condición que conlleva algunas implicaciones de interacción, como la depuración histórica

- Para notificar al usuario que el sistema ha detectado problemas, por ejemplo, cuando una extensión está causando problemas de rendimiento

- Proporcionar al usuario una manera de tomar medidas fácilmente, como cuando el editor detecta que un archivo tiene pestañas y espacios combinados

##### <a name="do"></a>Sí:

- Mantenga el texto del mensaje de la barra de texto en corto y en el punto.

- Mantenga el texto en los vínculos y los botones concisos.

- Asegúrese de que las opciones de "acción" que se proporcionan a los usuarios son mínimas, mostrando solo las acciones necesarias.

##### <a name="dont"></a>No:

- Use una barra de información para ofrecer comandos estándar que se deben colocar en una barra de herramientas.

- Use una barra de información en lugar de un cuadro de diálogo modal.

- Cree un mensaje flotante fuera de una ventana.

- Usar varios las barras en varias ubicaciones dentro de la misma ventana.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>¿Se pueden mostrar varios las barras al mismo tiempo?
 Sí, se pueden mostrar varios las barras al mismo tiempo. Se mostrarán en el orden del primero en salir y en el primero en aparecer con la primera barra de barra que se muestra en la parte superior y las barras adicionales que se muestran a continuación.

 El usuario verá un máximo de tres las barras a la vez, después del cual, si hay más las barras disponibles, la región de la barra de información pasará a ser desplazable.

### <a name="creating-an-infobar"></a>Crear una barra de información
 La barra de barra tiene cuatro secciones, de izquierda a derecha:

- **Icono:** Aquí es donde se agregan los iconos que se desean mostrar para la barra de información, como un icono de advertencia.

- **Texto:** Puede Agregar texto para describir el escenario o la situación en la que se encuentra el usuario, junto con los vínculos dentro del texto, si es necesario. Recuerde mantener el texto conciso.

- **Acciones:** Esta sección debe contener vínculos y botones para las acciones que el usuario puede realizar en la barra de barra.

- **Botón Cerrar:** La última sección de la derecha puede tener un botón Cerrar.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Crear una barra de barra estándar en código administrado
 La clase InfoBarModel se puede usar para crear un origen de datos para una barra de información. Use uno de estos cuatro constructores:

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

 Este es un ejemplo que crea un InfoBarModel con texto con un hipervínculo, un botón de acción y un icono.

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Crear una barra de barra estándar en código nativo
 Implemente la interfaz IVsInfoBar para proporcionar una barra de información de código nativo.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Obtener un UIElement de barra de información desde una barra de información
 La implementación de InfoBarModel o IVsInfoBar son modelos de datos que se deben convertir en un objeto UIElement para que se muestren en la interfaz de usuario. Un UIElement se puede recuperar con el servicio SVsInfoBarUIFactory/IVsInfoBarUIFactory.

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
 Las barras se puede mostrar en una o varias de las siguientes ubicaciones:

- Ventanas de herramientas

- Dentro de una pestaña de documento

> [!IMPORTANT]
> Es posible colocar una barra de información para proporcionar un mensaje sobre el contexto global. Esto aparecería entre las barras de herramientas y el cuadro de documento. Esto no se recomienda porque provoca problemas con "salto y salto" del IDE y debe evitarse a menos que sea absolutamente necesario y sea adecuado.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Colocar una barra de información en un ToolWindowPane
 El método ToolWindowPane. AddInfoBar (IVsInfoBar) se puede usar para agregar una barra de información a una ventana de herramientas. Esta API puede Agregar una IVsInfoBar (de la que InfoBarModel es una implementación predeterminada) o una IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Colocar una barra de información en un documento o no ToolWindowPane
 Para colocar una barra de información en cualquier IVsWindowFrame, use la propiedad VSFPROPID_InfoBarHost para obtener el IVsInfoBarHost del marco y, a continuación, agregue el UIElement de barra de información.

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
 Para colocar una barra de información en la ventana principal, use el VSSPROPID_MainWindowInfoBarHost del servicio IVsShell para obtener el IVsInfoBarHost de la ventana principal y, a continuación, agregue el UIElement de barra de información.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>¿Sé cuándo el usuario realiza una acción en mi barra de información?
 Sí, se devolverá cada acción de evento al autor de la barra de información. Después, el autor de la barra de información debe tomar medidas en el IDE en función de la selección del usuario en la barra de información. Las barras se quitará automáticamente del host en el que se hizo clic en el botón Cerrar, pero se requiere trabajo adicional si es necesario quitar otros las barras después del cierre. También será necesario registrar la telemetría de forma independiente en cada barra de barra.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Recepción de eventos de barra de la barra de ToolWindowPane
 ToolWindowPane tiene dos eventos para las barras. El evento InfoBarClosed se genera cuando se cierra una barra de información en ToolWindowPane. El evento InfoBarActionItemClicked se genera cuando se hace clic en un hipervínculo o botón dentro de la barra de la barra de la barra de la barra de

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Recepción de eventos de barra de barra directamente desde UIElement
 IVsInfoBarUIElement. Advise se puede usar para suscribirse a eventos directamente desde el UIElement de una barra de información. La implementación de IVsInfoBarUIEvents permitirá que el autor reciba eventos de cierre y clic.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> Validación de errores
 Cuando un usuario escribe información que no es aceptable, como cuando se omite un campo obligatorio o cuando los datos se escriben en el formato incorrecto, es mejor usar la validación de controles o comentarios cerca del control en lugar de usar un cuadro de diálogo de error de bloqueo emergente.

### <a name="field-validation"></a>Validación de campos
 La validación de formularios y campos consta de tres componentes: un control, un icono y una información sobre herramientas. Aunque varios tipos de controles pueden utilizarlo, se usará un cuadro de texto como ejemplo.

 ![La validación de campos &#40;en blanco&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Si el campo es obligatorio, debe haber texto de marca de agua que indique **\<Required>** y el fondo del campo debe ser amarillo claro (VSColor: `Environment.ControlEditRequiredBackground` ) y el primer plano debe ser gris (VSColor: `Environment.ControlEditRequiredHintText` ):

 ![Validación de campo con la etiqueta "Obligatorio"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 El programa puede determinar que el control se encuentra en un estado de *contenido no válido especificado* cuando se mueve el foco a otro control o cuando el usuario hace clic en un botón de confirmación [Aceptar] o cuando el usuario guarda el documento o formulario.

 Cuando se determina el estado de contenido no válido, aparece un icono en el control o justo junto a él. La información sobre herramientas que describe el error debe aparecer al mantener el puntero sobre el icono o el control. Además, debe aparecer un borde de 1 píxel alrededor del control que está creando el estado no válido.

 ![Especificaciones de diseño de validación de campo](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Especificaciones de diseño para la validación de campos**

#### <a name="acceptable-variations-for-icon-location"></a>Variaciones aceptables para la ubicación del icono
 Hay innumerables casos únicos en los que es necesario informar a los usuarios sobre los errores de validación. Teniendo en cuenta el tipo de control y la configuración de la interfaz de usuario, elija la ubicación del icono correspondiente a su situación.

 ![Ubicaciones aceptables para la ubicación del icono](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Variaciones aceptables para las ubicaciones de los iconos de validación de campos**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validación que requiere un recorrido de ida y vuelta a un servidor o una conexión de red
 En algunos casos, se requiere un recorrido de ida y vuelta al servidor para comprobar el contenido y es importante mostrar los Estados de progreso, comprobado y error del usuario. En la ilustración siguiente se muestra un ejemplo de este caso y la interfaz de usuario recomendada.

 ![Validación que implica un viaje de ida y vuelta a un servidor](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Validación que implica un viaje de ida y vuelta a un servidor**

 Tenga en cuenta que se debe proporcionar un espacio disponible adecuado a la derecha del control para dar cabida a la "comprobación..." y el texto "Reintentar".

#### <a name="in-place-warning-text"></a>Texto de advertencia en contexto
 Cuando haya espacio disponible para poner el mensaje de error cerca del control en un estado de error, es preferible usar solo la información sobre herramientas.

 ![En&#45;ADVERTENCIA de lugar](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Texto de advertencia en contexto**

#### <a name="watermarks"></a>Marcas de agua
 A veces, un control o ventana completo tiene un estado de error. En esta situación, use una marca de agua para indicar el error.

 ![Marca de agua](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Validación de campo de marca de agua**
