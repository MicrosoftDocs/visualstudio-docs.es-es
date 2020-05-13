---
title: Notificaciones y progreso para Visual Studio ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f6a7ddd5d1a5a7257617b03098722e1341017b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699880"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Notificaciones y progreso para Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a>Sistemas de notificación

### <a name="overview"></a>Información general
 Hay varias maneras de informar al usuario lo que está sucediendo en Visual Studio con respecto a sus tareas de desarrollo de software.

 Al implementar cualquier tipo de notificación:

- **Mantenga el número de notificaciones al** número mínimo efectivo. Los mensajes de notificación deben aplicarse a la mayoría de los usuarios de Visual Studio o a los usuarios de un área de características o características específica. El uso excesivo de notificaciones puede desviar al usuario o disminuir la facilidad de uso percibida del sistema.

- **Asegúrese** de que está presentando mensajes claros y procesables que el usuario puede usar para invocar el contexto adecuado para tomar decisiones más complejas y tomar medidas adicionales.

- **Presente mensajes sincrónicos y asincrónicos de forma adecuada.** Las notificaciones sincrónicas indican que algo necesita atención inmediata, como cuando se bloquea un servicio web o se produce una excepción de código. El usuario debe ser informado de esas situaciones de inmediato de una manera que requiera su entrada, como en un cuadro de diálogo modal. Las notificaciones asincrónicas son las que el usuario debe conocer pero que no deben tener que actuar de inmediato, como cuando finaliza una operación de compilación o finaliza una implementación de sitio web. Esos mensajes deben ser más ambiente y no interrumpir el flujo de tareas del usuario.

- **Utilice los cuadros de diálogo modales solo cuando sea necesario para evitar que el usuario realice más acciones** antes de reconocer el mensaje o tomar una decisión presentada en el cuadro de diálogo.

- **Elimine las notificaciones ambientales cuando ya no sean válidas.** No exija al usuario que descarte una notificación si ya ha tomado medidas para abordar el problema sobre el que se le notificó.

- **Tenga en cuenta que las notificaciones pueden dar lugar a correlaciones falsas.** Los usuarios pueden creer que una o más de sus acciones ha activado una notificación cuando en realidad no había ninguna relación causal. Sea claro en el mensaje de notificación sobre el contexto, el desencadenador y el origen de la notificación.

### <a name="choosing-the-right-method"></a>Elegir el método correcto
 Utilice esta tabla para ayudarle a elegir el método adecuado para notificar al usuario de su mensaje.

|Método|Uso|No debe usarse|
|------------|---------|----------------|
|[Diálogos de mensajes de error modales](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Se usa cuando se requiere una respuesta del usuario antes de continuar.|No lo utilice cuando no sea necesario bloquear al usuario e interrumpir su flujo. Evite utilizar cuadros de diálogo modales si es posible mostrar el mensaje de otra manera menos intrusiva.|
|[Barra de estado IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Se utiliza cuando hay información textual ambiental sobre el estado de un proceso.|No lo use solo. Se utiliza mejor junto con otro mecanismo de retroalimentación.|
|[Barra de información incrustada](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|En una ventana de herramientas o una ventana de documento, utilice para notificar el progreso, el estado de error, los resultados y/o la información procesable.|No utilizar si la información no es relevante para la ubicación donde se coloca la barra de información.<br /><br /> No utilice fuera de una ventana de documento/herramienta.|
|[Cambios en el cursor del ratón](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Se puede utilizar para notificar que un proceso está en curso. También se utiliza para notificar que hay un cambio de estado en el mouse, como cuando arrastrar/soltar está en curso o que el cursor del ratón está en un modo determinado, como el modo de dibujo.|No lo utilice para cambios de progreso cortos o si es probable que se aletee el cursor (por ejemplo, cuando está vinculado a partes de un proceso de ejecución más largo en lugar de a todo el proceso).|
|[Indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Utilícelo cuando necesite informar de progreso (ya sea determinado o indeterminado). Hay una variedad de tipos de indicadores de progreso y uso específico para cada uno. Consulte [Indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Ventana de notificaciones de Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La ventana Notificaciones no es extensible públicamente. Sin embargo, se usa para comunicar una serie de mensajes sobre Visual Studio, incluidos problemas críticos con la licencia y notificaciones informativas de actualizaciones a Visual Studio o a paquetes.|No usar para otros tipos de notificaciones.|
|[Lista de errores](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Cuando el problema se relaciona directamente con la solución actualmente abierta del usuario que tiene un problema (error/advertencia/información), es posible que deba tomar medidas en el código.<br /><br /> Esto incluiría, por ejemplo:<br /><br /> - Mensajes del compilador (error/advertencia/info)<br /><br /> - Analizador de código / Mensajes de diagnóstico sobre el código<br /><br /> - Construir mensajes<br /><br /> Puede ser adecuado para problemas relacionados con los archivos de proyecto o solución, pero considere primero una indicación del Explorador de soluciones.|No usar para elementos que no tienen ninguna relación con el código de solución abierto del usuario.|
|Notificaciones del editor: Bombilla de luz|Se usa cuando tiene una corrección disponible para solucionar un problema que existe en el archivo abierto.<br /><br /> Tenga en cuenta que la bombilla también se debe usar para hospedar acciones rápidas que se toman en el código del usuario a petición, como las refactorizaciones, pero en ese caso no aparecerá "estilo de notificación."|No utilizar para elementos que no tienen ninguna relación con el archivo abierto.|
|Notificaciones del editor: Squiggles|Se utiliza para alertar al usuario de un problema con un intervalo determinado de su código abierto (por ejemplo, un ondulado rojo para errores).|No usar para elementos que no se relacionan con un intervalo determinado de su código abierto.|
|[Barras de estado integradas](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Se utiliza para proporcionar el estado relacionado con el contenido o el proceso en el contexto de una ventana de herramientas, una ventana de documento o una ventana de diálogo específicas.|No utilice para notificaciones generales de productos, procesos o elementos que no tengan ninguna relación con el contenido dentro de la ventana específica.|
|[Notificaciones de bandejas de Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Se utiliza para exponer notificaciones para procesos fuera de proceso o aplicaciones complementarias.|No usar para las notificaciones que son relevantes para el IDE.|
|[Burbujas de notificación](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Se usa para notificar un proceso remoto o cambiar **fuera** del IDE.|No utilizar como medio para notificar al usuario de los procesos **dentro** del IDE.|

### <a name="notification-methods"></a>Métodos de notificación

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>Diálogos de mensajes de error modales
 Se utiliza un cuadro de diálogo de mensaje de error modal para mostrar un mensaje de error que requiere la confirmación o la acción del usuario.

 ![Mensaje de error modal](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Un cuadro de diálogo de mensaje de error modal que alerta al usuario de una cadena de conexión no válida a una base de datos**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>Barra de estado IDE
 La probabilidad de que los usuarios noten el texto de la barra de estado se correlaciona con su experiencia informática integral y experiencia específica con la plataforma Windows. La base de clientes de Visual Studio tiende a experimentarse en ambas áreas, aunque incluso los usuarios de Windows bien informados podrían perder los cambios en la barra de estado. Por lo tanto, la barra de estado se utiliza mejor con fines informativos o como una señal redundante para la información presentada en otro lugar. Cualquier tipo de información crítica que el usuario debe resolver inmediatamente debe proporcionarse en un cuadro de diálogo o en la ventana de la herramienta Notificaciones.

 La barra de estado de Visual Studio está diseñada para permitir que se muestren varios tipos de información. Se divide en regiones para comentarios, diseñador, barra de progreso, animación y cliente.

 La región de comentarios y la región del diseñador siempre están visibles. La barra de progreso y las regiones de animación siempre son dinámicas y se basan en el contexto del usuario. La región del diseñador tiene un ancho estático determinado por la longitud de la cadena que se extrae de un recurso adjunto para el mensaje de texto. Esto permite que la localización cambie el tamaño del ancho sin necesidad de un cambio de código. Para inglés, el ancho de esta cadena es de aproximadamente 220 píxeles. La región del diseñador se comportará normalmente y la región de comentarios absorberá el espacio restante.

 La barra de estado también se colorea para agregar interés visual y valor funcional mediante la comunicación de varios cambios de estado IDE, como cuando el IDE está en modo de depuración.

 ![Cambios de color de la barra de estado IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Colores de la barra de estado del IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>Barra de información integrada
 Una barra de información se puede utilizar en la parte superior de una ventana de documento o ventana de herramientas para informar al usuario de un estado o condición. También puede ofrecer comandos para que el usuario pueda tener una manera de tomar medidas fácilmente. La barra de información es un control de vaciado estándar. Evite crear el suyo propio, que actuará y parecerá incoherente con otros en el IDE. Consulte [Barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) para obtener detalles de implementación y orientación sobre el uso.

 ![Barra de información incrustada](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Una barra de información incrustada en una ventana de documento, alertando al usuario de que el IDE está en modo de depuración histórica y el editor no responderá de la misma manera que lo hace en el modo de depuración estándar.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>Cambios en el cursor del ratón
 Al cambiar el cursor del mouse, utilice colores que estén vinculados al servicio VSColor y que ya estén asociados con el cursor. Los cambios del cursor se pueden utilizar para indicar una operación en curso, así como zonas de posicionamiento donde el usuario está pasando el cursor sobre un destino que se puede arrastrar, colocar o utilizar para seleccionar un objeto.

 Utilice el cursor del ratón ocupado/espera solo cuando se debe reservar todo el tiempo de CPU disponible para una operación, lo que impide que el usuario exprese cualquier otra entrada. En la mayoría de los casos con aplicaciones bien escritas que utilizan multithreading, las horas en las que se impide a los usuarios realizar otras operaciones deben ser poco frecuentes.

 Tenga en cuenta que los cambios de cursor son útiles como una señal redundante para la información presentada en otro lugar. No confíe en un cambio de cursor como la única forma de comunicarse con el usuario, especialmente cuando intenta transmitir algo que es crítico que el usuario debe abordar.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>Indicadores de progreso
 Los indicadores de progreso son importantes para proporcionar a los usuarios comentarios durante los procesos que tardan más de unos segundos en completarse. Los indicadores de progreso se pueden mostrar in situ (cerca del punto de inicio de la acción en curso), en una barra de estado incrustada, en un cuadro de diálogo modal o en la barra de estado de Visual Studio. Siga las instrucciones en [Los indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) con respecto a su uso e implementación.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Ventana Notificaciones de Visual Studio
 La ventana Notificaciones de Visual Studio notifica a los desarrolladores acerca de las licencias, el entorno (Visual Studio), las extensiones y las actualizaciones. Los usuarios pueden descartar notificaciones individuales o pueden optar por ignorar ciertos tipos de notificaciones. La lista de notificaciones omitidas se administra en una página **Herramientas > opciones.**

 La ventana Notificaciones no es actualmente extensible.

 ![Ventana de notificaciones de Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Ventana de la herramienta Notificaciones de Visual Studio**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a>Lista de errores
 Una notificación dentro de la lista de errores indica errores y advertencias que se produjeron durante la compilación y el proceso de compilación y permite al usuario navegar en el código a ese error de código específico.

 ![Lista de errores](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Lista de errores en Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>Barras de estado integradas
 Dado que la barra de estado IDE es dinámica, con su contexto de región de cliente establecido en la ventana de documento activo y la actualización de información sobre el contexto del usuario o las respuestas del sistema, es difícil mantener una visualización continua de la información o dar estado en los procesos asincrónicos a largo plazo. Por ejemplo, la barra de estado IDE no es adecuada para las notificaciones de resultados de ejecución de pruebas para varias ejecuciones o selecciones de elementos inmediatamente procesables. Es importante conservar dicha información de estado en el contexto del documento o ventana de herramientas donde el usuario realiza una selección o inicia un proceso.

 ![Barra de estado incrustada](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Barra de estado incrustada en Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Notificaciones de bandejas de Windows
 El área de notificación de Windows está junto al reloj del sistema en la barra de tareas de Windows. Muchas utilidades y componentes de software proporcionan iconos en esta área para que el usuario pueda obtener un menú contextual para las tareas de todo el sistema, como cambiar la resolución de pantalla u obtener actualizaciones de software.

 Las notificaciones de nivel de entorno deben aparecer en el centro de notificaciones de Visual Studio, no en el área de notificación de Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>Burbujas de notificación
 Las burbujas de notificación pueden aparecer como informativas dentro de un editor/diseñador o como parte del área Notificación de Windows. El usuario percibe estas burbujas como problemas que pueden resolver más adelante, lo que es un beneficio para las notificaciones no críticas. Las burbujas son inapropiadas para la información crítica que el usuario debe resolver de inmediato. Si usa burbujas de notificación en Visual Studio, siga las instrucciones de Escritorio de Windows para las burbujas de [notificación.](/windows/desktop/uxguide/mess-notif)

 ![Burbuja de notificación](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Burbuja de notificación en el área Notificación de Windows utilizada para Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>Indicadores de progreso

### <a name="overview"></a>Información general
 Los indicadores de progreso son una parte importante de un sistema de notificación para dar comentarios a los usuarios. Indican al usuario cuándo se completarán los procesos y las operaciones. Los tipos de indicadores conocidos incluyen barras de progreso, cursores giratorios e iconos animados. El tipo y la colocación de un indicador de progreso depende del contexto, incluyendo lo que se está notificando y cuánto tiempo tardará el proceso u operación en completarse.

#### <a name="factors"></a>Factores
 Para determinar qué tipo de indicador es apropiado, debe determinar los siguientes factores.

1. **Tiempo:** duración de la operación

2. **Modalidad:** si la operación es modal al entorno (bloquea la interfaz de usuario hasta que se completa el proceso)

3. **Persistente/Transitorio:** si el resultado final del progreso debe ser reportado y/o visible en un momento posterior

4. **Determinado/Indeterminado:** si se puede calcular la hora de finalización y el progreso de la operación

5. **Ubicación gráfica/textual:** si el progreso o el proceso se captura en línea, en el cuerpo de un mensaje o en un control específico, como el control Tree

6. **Proximidad:** si el progreso debe estar muy cerca de la interfaz de usuario con la que está relacionado. (Por ejemplo, ¿puede estar en la barra de estado, que podría estar lejos, o tiene que estar cerca del botón que inició el proceso?)

#### <a name="determinate-progress"></a>Progreso determinado

|Tipo de progreso|Cuándo y cómo usar|Notas|
|-------------------|-------------------------|-----------|
|Barra de progreso (determinada)|Duración prevista de >5 segundos.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**NO** inserte texto en la animación.|
|Barra de información|Mensajería asociada a la interfaz de usuario contextual. Consulte [Barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**NO** utilice varias barras de información cuando necesite indicar varios procesos. Utilice barras de progreso apiladas en su lugar.|
|Ventana de salida|Notificación transitoria: proceso de nivel de aplicación del que el usuario desea **revisar** los detalles después de la finalización.|**NO** utilice si el usuario tendrá que hacer referencia a los datos más adelante.|
|Archivo de registro|Emparejado con notificación intransitoria en los casos en que es importante **guardar** los detalles después de la finalización.||
|Barra de estado|Notificación transitoria: proceso de nivel de aplicación que el usuario **no necesitará** detalles de después de la finalización.<br /><br /> Incluye una barra de progreso incrustada.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||

#### <a name="indeterminate-progress"></a>Progreso indeterminado

|Tipo de progreso|Cuándo y cómo usar|Notas|
|-------------------|-------------------------|-----------|
|Barra de progreso (indeterminada)|Duración prevista de >5 segundos.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**NO** inserte texto en la animación.|
|Hormigas (puntos horizontales animados)|Viaje de ida y vuelta al servidor.<br /><br /> Se coloca cerca del punto de contexto en la parte superior del contenedor principal.|**NO** lo use si no es padre de todo el contenedor.|
|Spinner (anillo de progreso)|Proceso asociado con la interfaz de usuario contextual o donde el espacio es una consideración.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||
|Barra de información|Mensajería asociada a la interfaz de usuario contextual. Consulte [Barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**NO** utilice varias barras de información cuando necesite indicar varios procesos. Utilice barras de progreso apiladas en su lugar.|
|Ventana de salida|Notificación transitoria: proceso de nivel de aplicación que el usuario querrá **revisar** los detalles de después de la finalización.|**NO se** use para obtener información que desee conservar entre sesiones.|
|Archivo de registro|Emparejado con notificación intransitoria en los casos en que es importante **guardar** los detalles después de la finalización.||
|Barra de estado|Notificación transitoria: proceso de nivel de aplicación que el usuario **no necesitará** detalles de después de la finalización.<br /><br /> Incluye barra de progreso incrustada.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||

### <a name="progress-indicator-types"></a>Tipos de indicadores de progreso

#### <a name="progress-bars"></a>Barras de progreso

##### <a name="indeterminate"></a>Indeterminado
 ![Barra de progreso indeterminado](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Barra de progreso indeterminado**

 "Indeterminado" significa que no se puede determinar el progreso general de una operación o proceso. Utilice barras de progreso indeterminadas para operaciones que requieran una cantidad de tiempo sin límites o que tienen acceso a un número desconocido de objetos. Utilice una descripción textual para acompañar lo que está sucediendo. Use tiempos de espera para dar límites a operaciones basadas en tiempo. Las barras de progreso indeterminadas utilizan animaciones para mostrar que se está progresando, pero no proporcionan otra información. No elija una barra de progreso indeterminada basada únicamente en la posible falta de precisión por sí sola.

##### <a name="determinate"></a>Determinados
 ![Barra de progreso determinada](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Barra de progreso determinada**

 "Determinado" significa que una operación o proceso requiere una cantidad limitada de tiempo, incluso si esa cantidad de tiempo no se puede predecir con precisión. Indique claramente la finalización. No permita que una barra de progreso vaya al 100 por ciento a menos que la operación se haya completado. La animación de la barra de progreso determinada se mueve de izquierda a derecha de 0 a 100%.

 Nunca mueva el indicador de progreso hacia atrás durante una operación. La barra debe avanzar hacia adelante constantemente cuando la operación comienza y alcanzar el 100% cuando termina. El punto de la barra de progreso es dar al usuario una idea de cuánto tiempo tarda toda la operación, independientemente de cuántos pasos estén involucrados.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Informes simultáneos (barras de progreso apiladas)
 Si una operación tarda mucho tiempo - tal vez varios minutos - entonces se pueden utilizar dos barras de progreso, una que muestra el progreso general de una operación y otra para la progresión del paso actual. Por ejemplo, si un programa de instalación está copiando muchos archivos, se puede utilizar una barra de progreso para indicar cuánto tiempo tarda todo el proceso, mientras que un segundo puede indicar qué porcentaje del archivo o directorio actual se está copiando. No informe de más de cinco operaciones o procesos simultáneos mediante barras de progreso apiladas. Si tiene más de cinco operaciones o procesos simultáneos para informar, utilice un cuadro de diálogo modal con un botón Cancelar e informe de los detalles de progreso a la ventana de salida.

##### <a name="textual-descriptions"></a>Descripciones textuales
 Utilice una descripción textual para acompañar lo que está sucediendo y el tiempo estimado hasta su finalización. Si es imposible determinar cuánto tiempo tardará una operación, entonces una mejor opción para dar comentarios podría ser un icono animado en lugar de una barra de progreso.

 Visual Studio proporciona una barra de progreso estándar en la barra de estado que puede usar cualquier producto integrado en Visual Studio. Para las descripciones textuales de lo que está sucediendo mientras se anima la barra de progreso, el texto de la barra de estado se puede actualizar.

#### <a name="other-progress-indicators"></a>Otros indicadores de progreso

##### <a name="ants-animated-horizontal-dots"></a>Hormigas (puntos horizontales animados)
 ![Hormigas de progreso](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Ants", los puntos horizontales animados, proporcionan una referencia visual para un proceso de servidor de ida y vuelta indeterminado.

##### <a name="spinner-progress-ring"></a>Spinner (anillo de progreso)
 ![Control giratorio de progreso](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 El spinner (también conocido como "anillo de progreso") es un indicador de progreso indeterminado utilizado principalmente en relación con la interfaz de usuario contextual. Mostrar un spinner muy cerca de su contenido relacionado, como un encabezado de categoría textual, mensajería o control.

##### <a name="cursor-feedback"></a>Retroalimentación del cursor
 Para las operaciones que tardan entre 2 y 7 segundos, proporcione comentarios del cursor. Normalmente, esto significa usar el cursor de espera proporcionado por el sistema operativo. Para obtener instrucciones, vea el artículo de MSDN [Cursors.Wait (Propiedad).](/dotnet/api/system.windows.input.cursors.wait)

#### <a name="progress-indicator-locations"></a>Ubicaciones de los indicadores de progreso

##### <a name="status-bar"></a>Barra de estado
 La barra de estado proporciona a la aplicación un lugar para mostrar mensajes e información útil al usuario sin interrumpir el trabajo del usuario. Normalmente se muestra en la parte inferior de una ventana, el estado del progreso será un panel de información sobre herramientas que incluye un mensaje sobre la medida del progreso en combinación con un indicador de barra de progreso.

 ![Barra de estado con barra de progreso](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Barra de estado con barra de progreso**

 ![Barra de estado con mensajes](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Barra de estado con descripción textual**

##### <a name="infobar"></a>Barra de información
 Al igual que la barra de estado, la barra de información proporciona notificación contextual y mensajería, que también se puede emparejar con indicadores de progreso indeterminados, como la barra de progreso o el spinner. La barra de información no debe proporcionar un progreso de nivel granular ni una indicación de progreso determinada. Consulte [Barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Barra de información con barra y mensajes de progreso](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Barra de información con barra de progreso y descripción textual**

 ![Barra de información dentro de una ventana](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>En línea
 La indicación de progreso en línea se puede representar mediante cualquiera de los tipos de cargador de progreso. Normalmente, el indicador de progreso se empareja con la mensajería, pero esto no es un requisito.

 ![Control giratorio de progreso en línea](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Spinner combinado con descripción textual**

 ![Barras de progreso apiladas en línea](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Barra de progreso apiladas determinadas**

 ![Mensajes de progreso en línea](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Texto en línea del Explorador de servidores: Actualizar...**

##### <a name="tool-windows"></a>Ventanas de herramientas
 La indicación de progreso global se representa mediante una barra de progreso indeterminada situada directamente debajo de la barra de herramientas.

 ![Barra de progreso indeterminada global](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Barra de progreso indeterminada global de Team Explorer**

##### <a name="dialogs"></a>Cuadros de diálogo
 Los cuadros de diálogo pueden contener cualquiera de los tipos de cargador de progreso. Los indicadores de progreso se pueden emparejar con mensajería, así como combinarse con múltiples niveles de indicación de progreso para representar procesos granulares y sub-procesos.

 ![Cuadro de diálogo con varios tipos de indicador de progreso](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Cuadro de diálogo de Visual Studio con procesos simultáneos y varios tipos de indicadores de progreso**

 ![Cuadro de diálogo con cargador y mensajes de progreso](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Diálogo de Visual Studio con cargador de progreso y comandos en línea de mensajería**

##### <a name="document-well"></a>Documento bien
 El pozo de documentos puede mostrar varios tipos de cargadores de progreso en combinación con controles.

 ![Mensajes de progreso en la sección de documentos](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Barra de progreso indeterminada debajo de la barra de herramientas**

##### <a name="output-window"></a>Ventana de salida
 La ventana Salida es adecuada para controlar la progresión del proceso y el estado de progreso continuo a través de la mensajería textual en línea. Debe utilizar la barra Estado junto con cualquier informe de progreso de la ventana de salida.

 ![Mensajes de progreso en la ventana de salida](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Ventana de salida con estado de proceso continuo y mensajería de espera**

## <a name="infobars"></a><a name="BKMK_Infobars"></a>Barras de información

### <a name="overview"></a>Información general
 Las barras de información proporcionan al usuario un indicador cercano a su punto de atención y el uso del control de la barra de información compartida garantiza la coherencia en la apariencia visual y la interacción.

 ![Barra de información](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Infobars en Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Usos adecuados para una barra de información

- Para dar al usuario un mensaje importante y sin bloqueo relevante para el contexto actual

- Para indicar que la interfaz de usuario está en un determinado estado o condición que contiene algunas implicaciones de interacción, como la depuración histórica

- Notificar al usuario que el sistema ha detectado problemas, como cuando una extensión está causando problemas de rendimiento

- Proporcionar al usuario una forma de tomar medidas fácilmente, como cuando el editor detecta que un archivo tiene pestañas y espacios mixtos

##### <a name="do"></a>Sí:

- Mantenga el texto del mensaje de la barra de información corto y al punto.

- Mantenga el texto en enlaces y botones sucintos.

- Asegúrese de que las opciones de "acción" que proporcione a los usuarios sean mínimas, lo que muestra solo las acciones necesarias.

##### <a name="dont"></a>No:

- Utilice una barra de información para ofrecer comandos estándar que se deben colocar en una barra de herramientas.

- Utilice una barra de información en lugar de un cuadro de diálogo modal.

- Cree un mensaje flotante fuera de una ventana.

- Utilice varias barras de información en varias ubicaciones dentro de la misma ventana.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>¿Pueden mostrarse varias barras de información al mismo tiempo?
 Sí, varias barras de información pueden mostrarse al mismo tiempo. Se mostrarán por orden de llegada con la primera barra de información que aparece en la parte superior y barras de información adicionales que se muestran a continuación.

 El usuario verá un máximo de tres barras de información a la vez, después de lo cual, si hay más barras de información disponibles, la región de la barra de información se convertirá en desplazable.

### <a name="creating-an-infobar"></a>Creación de una barra de información
 La barra de información tiene cuatro secciones, de izquierda a derecha:

- **Icono:** Aquí es donde agregarías cualquier icono que quieras mostrar para la barra de información, como un icono de advertencia.

- **Texto:** Puede agregar texto para describir el escenario o la situación en la que se encuentra el usuario, junto con vínculos dentro del texto, si es necesario. Recuerde mantener el texto sucinto.

- **Acciones:** Esta sección debe contener enlaces y botones para las acciones que el usuario puede realizar en la barra de información.

- **Botón Cerrar:** La última sección a la derecha puede tener un botón de cierre.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Creación de una barra de información estándar en código administrado
 La clase InfoBarModel se puede utilizar para crear un origen de datos para una barra de información. Utilice uno de estos cuatro constructores:

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Creación de una barra de información estándar en código nativo
 Implemente la interfaz IVsInfoBar para proporcionar una barra de información desde código nativo.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Obtener una barra de información UIElement desde una barra de información
 El InfoBarModel o IVsInfoBar implementación son modelos de datos que se deben convertir en un UIElement para que se muestre en la interfaz de usuario. Un UIElement se puede recuperar con el SVsInfoBarUIFactory/IVsInfoBarUIFactory servicio.

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
 Las barras de información se pueden mostrar en una o más de las siguientes ubicaciones:

- Ventanas de herramientas

- Dentro de una pestaña de documento

> [!IMPORTANT]
> Es posible colocar una barra de información para dar un mensaje sobre el contexto global. Esto aparecería entre las barras de herramientas y el documento bien. Esto no se recomienda porque causa problemas con "salto y tirón" del IDE y debe evitarse a menos que sea absolutamente necesario y apropiado.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Colocar una barra de información en un ToolWindowPane
 El ToolWindowPane.AddInfoBar(IVsInfoBar) método se puede utilizar para agregar una barra de información a una ventana de herramientas. Esta API puede agregar un IVsInfoBar (de los cuales InfoBarModel es una implementación predeterminada) o un IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Colocar una barra de información en un documento o en un panel que no sea ToolWindowPane
 Para colocar una barra de información en cualquier IVsWindowFrame, use la propiedad VSFPROPID_InfoBarHost para obtener el IVsInfoBarHost para el marco y, a continuación, agregue la barra de información UIElement.

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

#### <a name="placing-an-infobar-in-the-main-window"></a>Colocación de una barra de información en la ventana principal
 Para colocar una barra de información en la ventana principal, use la VSSPROPID_MainWindowInfoBarHost del servicio IVsShell para obtener IVsInfoBarHost de la ventana principal y, a continuación, agregue la barra de información UIElement a ella.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>¿Sabré cuándo el usuario realiza una acción en mi barra de información?
 Sí, devolveremos cada acción de evento al autor de la barra de información. A continuación, depende del autor de la barra de información para realizar una acción en el IDE en función de la selección del usuario en la barra de información. Las barras de información se eliminarán automáticamente del host en el que se hizo clic en el botón Cerrar, pero se requiere trabajo adicional si es necesario eliminar otras barras de información después de cerrar. La telemetría también tendrá que ser registrada independientemente por cada barra de información.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Recepción de eventos de barra de información en un ToolWindowPane
 ToolWindowPane tiene dos eventos para las barras de información. El evento InfoBarClosed se produce cuando se cierra una barra de información en El ToolWindowPane. El evento InfoBarActionItemClicked se produce cuando se hace clic en un hipervínculo o botón dentro de la barra de información.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Recepción de eventos de barra de información directamente desde UIElement
 IVsInfoBarUIElement.Advise se puede utilizar para suscribirse a eventos directamente desde UIElement de una barra de información. Implementar IVsInfoBarUIEvents permitirá al autor recibir eventos de cierre y clic.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a>Validación de errores
 Cuando un usuario escribe información que no es aceptable, como cuando se omite un campo obligatorio o cuando se introducen datos en el formato incorrecto, es mejor usar la validación del control o comentarios cerca del control en lugar de usar un cuadro de diálogo de error emergente de bloqueo.

### <a name="field-validation"></a>Validación de campos
 La validación de formularios y campos consta de tres componentes: un control, un icono y una información sobre herramientas. Aunque varios tipos de controles pueden usar esto, se usará un cuadro de texto como ejemplo.

 ![Validación de campo &#40;&#41;en blanco](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Si el campo es obligatorio, debe ** \<** haber texto de marca de agua que `Environment.ControlEditRequiredBackground`indique Requerido>y el `Environment.ControlEditRequiredHintText`fondo del campo debe ser amarillo claro (VSColor: ) y el primer plano debe ser gris (VSColor: ):

 ![Validación de campo con la etiqueta "Obligatorio"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 El programa puede determinar que el control está en un estado de *contenido no válido introducido* cuando el foco se mueve a otro control o cuando el usuario hace clic en un botón de confirmación [OK] o cuando el usuario guarda el documento o formulario.

 Cuando se determina el estado de contenido no válido, aparece un icono dentro del control o justo al lado de él. Una información sobre herramientas que describe el error debe aparecer al mantener el mouse del icono o del control. Además, debe aparecer un borde de 1 píxel alrededor del control que está creando el estado no válido.

 ![Especificaciones de diseño de validación de campo](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Especificaciones de diseño para la validación de campo**

#### <a name="acceptable-variations-for-icon-location"></a>Variaciones aceptables para la ubicación del icono
 Hay innumerables casos únicos en los que los usuarios necesitan ser informados sobre los errores de validación. Teniendo en cuenta el tipo de control y la configuración de la interfaz de usuario, elija la ubicación del icono adecuada a su situación.

 ![Ubicaciones aceptables para la ubicación del icono](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Variaciones aceptables para ubicaciones de icono de validación de campo**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validación que requiere un viaje de ida y vuelta a un servidor o conexión de red
 En algunos casos, se requiere un viaje de ida y vuelta al servidor para verificar el contenido y sería importante mostrar el progreso del usuario, verificado y los estados de error. La figura siguiente muestra un ejemplo de este caso y la interfaz de usuario recomendada.

 ![Validación que implica un viaje de ida y vuelta a un servidor](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Validación que implica un viaje de ida y vuelta a un servidor**

 Tenga en cuenta que se debe proporcionar un espacio disponible adecuado a la derecha del control para dar cabida a la "Verificación..." y texto "Reintentar".

#### <a name="in-place-warning-text"></a>Texto de advertencia in situ
 Cuando hay espacio disponible para colocar el mensaje de error cerca del control en un estado de error, esto es preferible a usar la información sobre herramientas solo.

 ![En&#45;lugar de advertencia](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Texto de advertencia in situ**

#### <a name="watermarks"></a>Marcas de agua
 A veces, un control o ventana completo está en un estado de error. En esta situación, utilice una marca de agua para indicar el error.

 ![Watermark](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Validación del campo de marca de agua**
