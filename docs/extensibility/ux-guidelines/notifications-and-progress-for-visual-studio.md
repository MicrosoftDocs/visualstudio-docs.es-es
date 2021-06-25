---
title: Notificaciones y progreso de Visual Studio | Microsoft Docs
description: Obtenga información sobre varias maneras de informar a los usuarios de lo que sucede en Visual Studio con respecto a sus tareas de desarrollo de software.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 994a315d04b06d1998a8c8e0c4291b6a4c54cb61
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902246"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Notificaciones y progreso para Visual Studio
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Sistemas de notificación

### <a name="overview"></a>Información general
 Hay varias maneras de informar al usuario de lo que sucede en Visual Studio con respecto a sus tareas de desarrollo de software.

 Al implementar cualquier tipo de notificación:

- **Mantenga el número de notificaciones en el número mínimo** efectivo. Los mensajes de notificación deben aplicarse a la mayoría de Visual Studio usuarios o a los usuarios de un área de características o características específica. El uso excesivo de notificaciones puede desatrastar al usuario o disminuir la facilidad de uso perceptida del sistema.

- **Asegúrese de que presenta mensajes claros y** acciones que el usuario puede usar para invocar el contexto adecuado para tomar decisiones más complejas y tomar medidas.

- **Presente los mensajes sincrónicos y asincrónicos correctamente.** Las notificaciones sincrónicas indican que algo necesita atención inmediata, como cuando se bloquea un servicio web o se produce una excepción de código. El usuario debe estar informado inmediatamente de esas situaciones de una manera que requiera su entrada, como en un cuadro de diálogo modal. Las notificaciones asincrónicas son aquellas que el usuario debe conocer, pero no deben actuar inmediatamente, como cuando se completa una operación de compilación o cuando finaliza una implementación de sitio web. Esos mensajes deben ser más ambientales y no interrumpir el flujo de tareas del usuario.

- **Use diálogos modales solo** cuando sea necesario para impedir que el usuario tome medidas lejos de reconocer el mensaje o tomar una decisión presentada en el diálogo.

- **Quite las notificaciones de ambiente cuando ya no sean válidas.** No exija al usuario que descarte una notificación si ya ha tomado medidas para solucionar el problema sobre el que se le notificó.

- **Tenga en cuenta que las notificaciones pueden dar lugar a correlaciones falsas.** Los usuarios pueden pensar que una o varias de sus acciones han desencadenado una notificación cuando, de hecho, no hubo ninguna relación causal. Sea claro en el mensaje de notificación sobre el contexto, el desencadenador y el origen de la notificación.

### <a name="choosing-the-right-method"></a>Elección del método correcto
 Use esta tabla para ayudarle a elegir el método correcto para notificar al usuario su mensaje.

|Método|Usar|No debe usarse|
|------------|---------|----------------|
|[Cuadros de diálogo de mensajes de error modales](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Use cuando se requiera una respuesta del usuario antes de continuar.|No use cuando no sea necesario bloquear el usuario e interrumpir su flujo. Evite usar diálogos modales si es posible mostrar el mensaje de otra manera menos intrusiva.|
|[Barra de estado del IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Use cuando haya información textual ambiental relacionada con el estado de un proceso.|No use por sí solo. Se usa mejor junto con otro mecanismo de comentarios.|
|[Barra de información incrustada](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|En una ventana de herramientas o ventana de documento, use para notificar el progreso, el estado de error, los resultados o la información útil.|No use si la información no es relevante para la ubicación donde se coloca la barra de información.<br /><br /> No use fuera de una ventana de documento o herramienta.|
|[Cambios del cursor del mouse](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Se puede usar para notificar que un proceso está en proceso. También se usa para notificar que hay un cambio de estado en el mouse, como cuando la operación de arrastrar y colocar está en curso o que el cursor del mouse está en un modo determinado, como el modo de dibujo.|No use para cambios de progreso corto o si es probable que se alete el cursor (por ejemplo, cuando está vinculado a partes de un proceso de ejecución más larga en lugar de a todo el proceso).|
|[Indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Use cuando necesite notificar el progreso (ya sea determinado o indeterminado). Hay una variedad de tipos de indicadores de progreso y uso específico para cada uno. Consulte [Indicadores de progreso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Ventana de notificaciones de Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|La ventana Notificaciones no es extensible públicamente. Sin embargo, se usa para comunicar una variedad de mensajes sobre Visual Studio, incluidos los problemas críticos con la licencia y las notificaciones informativos de actualizaciones a Visual Studio o a paquetes.|No use para otros tipos de notificaciones.|
|[Lista de errores](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Cuando el problema se relaciona directamente con la solución abierta actualmente del usuario que tiene un problema (error, advertencia e información), es posible que deba tomar medidas en el código.<br /><br /> Esto incluiría, por ejemplo:<br /><br /> - Mensajes del compilador (error,advertencia/información)<br /><br /> - Analizador de código/Mensajes de diagnóstico sobre el código<br /><br /> - Generar mensajes<br /><br /> Puede ser adecuado para problemas relacionados con los archivos de proyecto o solución, pero considere primero Explorador de soluciones una indicación.|No use para los elementos que no tienen ninguna relación con el código de solución abierto del usuario.|
|Notificaciones del editor: Bombilla|Use cuando tenga una corrección disponible para solucionar un problema que existe en el archivo abierto.<br /><br /> Tenga en cuenta que bombilla también debe usarse para hospedar acciones rápidas que se toman en el código del usuario a petición, como refactorizaciones, pero en ese caso no aparecerá "estilo de notificación".|No use para los elementos que no tienen ninguna relación con el archivo abierto.|
|Notificaciones del editor: ondulados|Use para alertar al usuario de un problema con un intervalo determinado de su código abierto (por ejemplo, un ondulado rojo en busca de errores).|No use para los elementos que no están relacionados con un intervalo determinado de su código abierto.|
|[Barras de estado incrustadas](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Use para proporcionar el estado relacionado con el contenido o el proceso en el contexto de una ventana de herramientas, ventana de documento o ventana de diálogo específica.|No use para notificaciones generales de productos, procesos o elementos que no tengan ninguna relación con el contenido dentro de la ventana específica.|
|[Notificaciones de bandeja de Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Use para enviar notificaciones para procesos fuera de proceso o aplicaciones complementarias.|No use para las notificaciones que son relevantes para el IDE.|
|[Burbujas de notificación](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Use para notificar un proceso remoto o cambiar **fuera** del IDE.|No use como medio para notificar al usuario los procesos **dentro** del IDE.|

### <a name="notification-methods"></a>Métodos de notificación

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Cuadros de diálogo de mensajes de error modales
 Se usa un cuadro de diálogo de mensaje de error modal para mostrar un mensaje de error que requiere la confirmación o la acción del usuario.

 ![Mensaje de error modal](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Cuadro de diálogo de mensaje de error modal que alerta al usuario de una cadena de conexión no válida a una base de datos**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> Barra de estado del IDE
 La probabilidad de que los usuarios observen que el texto de la barra de estado se correlaciona con su experiencia de equipo completa y experiencia específica con la plataforma Windows. La Visual Studio base de clientes tiende a experimentarse en ambas áreas, aunque incluso los usuarios de Windows conocedores podrían perderse los cambios en la barra de estado. Por lo tanto, la barra de estado se usa mejor con fines informativos o como una indicación redundante para la información presentada en otro lugar. Cualquier tipo de información crítica que el usuario debe resolver inmediatamente debe proporcionarse en un cuadro de diálogo o en la ventana de la herramienta Notificaciones.

 La Visual Studio de estado está diseñada para permitir que se muestren varios tipos de información. Se divide en regiones para comentarios, diseñador, barra de progreso, animación y cliente.

 La región de comentarios y la región del diseñador siempre están visibles. La barra de progreso y las regiones de animación siempre son dinámicas y se basan en el contexto del usuario. La región del diseñador tiene un ancho estático determinado por la longitud de la cadena que se extrae de un recurso adjunto para el mensaje de texto. Esto permite que la localización cambie el tamaño del ancho sin necesidad de un cambio de código. En inglés, el ancho de esta cadena es de aproximadamente 220 píxeles. La región del diseñador se comportará con normalidad y la región de comentarios absorbirá el espacio restante.

 La barra de estado también se colorea para agregar interés visual y valor funcional mediante la comunicación de varios cambios de estado del IDE, como cuando el IDE está en modo de depuración.

 ![Cambios de color de la barra de estado IDE](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **Colores de la barra de estado del IDE**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Barra de información insertadas
 Se puede usar una barra de información en la parte superior de una ventana de documento o ventana de herramientas para informar al usuario de un estado o condición. También puede ofrecer comandos para que el usuario pueda tener una manera de realizar acciones fácilmente. La barra de información es un control de shell estándar. Evite crear el suyo propio, que actuará y parecerá incoherente con otros usuarios del IDE. Consulte [Barras de información para obtener detalles](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) de implementación e instrucciones de uso.

 ![Barra de información incrustada](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Una barra de información incrustada en una ventana de documento, que alerta al usuario de que el IDE está en modo de depuración histórica y el editor no responderá de la misma manera que en el modo de depuración estándar.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Cambios del cursor del mouse
 Al cambiar el cursor del mouse, use colores que estén asociados al servicio VSColor y que ya estén asociados al cursor. Los cambios de cursor se pueden usar para indicar una operación en curso, así como zonas de acceso en las que el usuario mantiene el puntero sobre un destino que se puede arrastrar, mover o usar para seleccionar un objeto.

 Use el cursor del mouse ocupado/espera solo cuando todo el tiempo de CPU disponible se deba reservar para una operación, lo que impide que el usuario exprese ninguna entrada adicional. En la mayoría de los casos con aplicaciones bien escritas que usan multithreading, las ocasiones en las que se impide que los usuarios puedan realizar otras operaciones deben ser poco frecuentes.

 Tenga en cuenta que los cambios de cursor son útiles como una indicación redundante de la información presentada en otra parte. No se base en un cambio de cursor como única manera de comunicarse con el usuario, especialmente al intentar transmitir algo crítico que el usuario debe abordar.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> Indicadores de progreso
 Los indicadores de progreso son importantes para proporcionar comentarios al usuario durante los procesos que tarden más de unos segundos en completarse. Los indicadores de progreso se pueden mostrar en su lugar (cerca del punto de inicio de la acción en curso), en una barra de estado incrustada, en un cuadro de diálogo modal o en la Visual Studio de estado. Siga las instrucciones de [Indicadores de progreso con](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) respecto a su uso e implementación.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio de notificaciones
 La ventana Visual Studio notificaciones notifica a los desarrolladores sobre licencias, entorno (Visual Studio), extensiones y actualizaciones. Los usuarios pueden descartar notificaciones individuales o pueden optar por omitir determinados tipos de notificaciones. La lista de notificaciones omitadas se administra en una **página Herramientas > opciones.**

 La ventana Notificaciones no es extensible actualmente.

 ![Ventana de notificaciones de Visual Studio](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio de herramientas Notificaciones**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Lista de errores
 Una notificación dentro de la lista de errores indica los errores y advertencias que se produjeron durante la compilación y el proceso de compilación, y permite al usuario navegar en el código hasta ese error de código específico.

 ![Lista de errores](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Lista de errores en Visual Studio**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Barras de estado incrustadas
 Dado que la barra de estado del IDE es dinámica, con su contexto de región de cliente establecido en la ventana de documento activa y la información que se actualiza en el contexto o las respuestas del sistema del usuario, es difícil mantener una presentación continua de información o proporcionar estado en procesos asincrónicos a largo plazo. Por ejemplo, la barra de estado del IDE no es adecuada para las notificaciones de los resultados de la ejecución de pruebas para varias ejecuciones o selecciones de elementos que se pueden actuar inmediatamente. Es importante conservar esta información de estado en el contexto de la ventana de documento o herramienta donde el usuario realiza una selección o inicia un proceso.

 ![Barra de estado incrustada](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Barra de estado incrustada en Visual Studio**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Notificaciones de bandeja de Windows
 El área de notificación de Windows está junto al reloj del sistema en la barra de tareas de Windows. Muchas utilidades y componentes de software proporcionan iconos en esta área para que el usuario pueda obtener un menú contextual para tareas de todo el sistema, como cambiar la resolución de pantalla u obtener actualizaciones de software.

 Las notificaciones de nivel de entorno deben estar en el centro Visual Studio notificaciones, no en el área de notificaciones de Windows.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Burbujas de notificación
 Las burbujas de notificación pueden aparecer como informativos dentro de un editor o diseñador o como parte del área de notificación de Windows. El usuario percibe estas burbujas como problemas que pueden resolver más adelante, lo que es una ventaja para las notificaciones no críticas. Las burbujas no son adecuadas para la información crítica que el usuario debe resolver de inmediato. Si usa burbujas de notificación en Visual Studio, siga las instrucciones del escritorio de Windows para [las burbujas de notificación.](/windows/desktop/uxguide/mess-notif)

 ![Burbuja de notificación](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Burbuja de notificación en el área de notificación de Windows que se usa para Visual Studio**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> Indicadores de progreso

### <a name="overview"></a>Información general
 Los indicadores de progreso son una parte importante de un sistema de notificación para proporcionar comentarios al usuario. Le dice al usuario cuándo se completarán los procesos y las operaciones. Los tipos de indicador conocidos incluyen barras de progreso, cursores giratorios e iconos animados. El tipo y la colocación de un indicador de progreso dependen del contexto, incluido lo que se notifica y cuánto tiempo se tardará en completarse el proceso o la operación.

#### <a name="factors"></a>Factores
 Para determinar qué tipo de indicador es adecuado, debe determinar los siguientes factores.

1. **Tiempo:** duración de la operación

2. **Modalidad: si** la operación es modal para el entorno (bloquea la interfaz de usuario hasta que se complete el proceso)

3. **Persistente o transitorio: indica** si el resultado final del progreso debe ser notificado o visualizable en un momento posterior.

4. **Determinación o indeterminación: si** se puede calcular la hora de finalización de la operación y el progreso

5. **Ubicación gráfica o textual:** si el progreso o el proceso se capturan en línea, en el cuerpo de un mensaje o en un control específico, como el control Árbol

6. **Proximidad: indica** si el progreso debe estar cerca de la interfaz de usuario con la que está relacionada. (Por ejemplo, ¿puede estar en la barra de estado, que podría estar lejos o tiene que estar cerca del botón que inició el proceso?)

#### <a name="determinate-progress"></a>Progreso determinado

|Tipo de progreso|Cuándo y cómo usar|Notas|
|-------------------|-------------------------|-----------|
|Barra de progreso (determinación)|Duración esperada de >5 segundos.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**NO inserte texto** en la animación.|
|Barra de información|Mensajería asociada a la interfaz de usuario contextual. Vea [Barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**NO use varias** barras de información cuando necesite indicar varios procesos. En su lugar, use barras de progreso apiladas.|
|Ventana de salida|Notificación transitoria: proceso de nivel de aplicación del que el usuario quiere **revisar los** detalles después de la finalización.|**NO use si** el usuario tendrá que hacer referencia a los datos más adelante.|
|Archivo de registro|Se empareja con la notificación intransigencia en los casos en los que es importante guardar **los** detalles después de la finalización.||
|Barra de estado|Notificación transitoria: proceso de nivel de aplicación del que el usuario **no necesitará detalles** después de la finalización.<br /><br /> Incluye una barra de progreso incrustada.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||

#### <a name="indeterminate-progress"></a>Progreso indeterminado

|Tipo de progreso|Cuándo y cómo usar|Notas|
|-------------------|-------------------------|-----------|
|Barra de progreso (indeterminado)|Duración esperada de >5 segundos.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.|**NO inserte texto** en la animación.|
|Ants (puntos horizontales animados)|Recorrido de ida y vuelta al servidor.<br /><br /> Se coloca cerca del punto de contexto en la parte superior del contenedor primario.|**NO use si** no está primario en todo el contenedor.|
|Spinner (anillo de progreso)|Proceso asociado a la interfaz de usuario contextual o donde el espacio es una consideración.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||
|Barra de información|Mensajería asociada a la interfaz de usuario contextual. Vea [Barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**NO use varias** barras de información cuando necesite indicar varios procesos. En su lugar, use barras de progreso apiladas.|
|Ventana de salida|Notificación transitoria: proceso de nivel de aplicación del que el usuario querrá revisar **los** detalles después de la finalización.|**NO use para** obtener información que necesite conservarse entre sesiones.|
|Archivo de registro|Emparejado con la notificación intransigencia en los casos en los que es importante guardar **los** detalles después de la finalización.||
|Barra de estado|Notificación transitoria: proceso de nivel de aplicación del que el usuario **no necesitará detalles** después de la finalización.<br /><br /> Incluye la barra de progreso incrustada.<br /><br /> Puede incluir una descripción textual de los detalles del proceso.||

### <a name="progress-indicator-types"></a>Tipos de indicadores de progreso

#### <a name="progress-bars"></a>Barras de progreso

##### <a name="indeterminate"></a>Indeterminado
 ![Barra de progreso indeterminada](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Barra de progreso indeterminada**

 "Indeterminado" significa que no se puede determinar el progreso general de una operación o un proceso. Use barras de progreso indeterminadas para operaciones que requieran una cantidad de tiempo sin enlazar o que accedan a un número desconocido de objetos. Use una descripción textual para acompaña a lo que sucede. Use tiempos de espera para proporcionar límites a las operaciones basadas en el tiempo. Las barras de progreso indeterminadas usan animaciones para mostrar que se está haciendo el progreso, pero no proporcionan ninguna otra información. No elija una barra de progreso indeterminada solo en función de la posible falta de precisión.

##### <a name="determinate"></a>Determinados
 ![Barra de progreso determinada](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Barra de progreso determinada**

 "Determinate" significa que una operación o un proceso requiere una cantidad limitada de tiempo, incluso si esa cantidad de tiempo no se puede predecir con precisión. Indique claramente la finalización. No permita que una barra de progreso vaya al 100 % a menos que se haya completado la operación. La animación de la barra de progreso determinada se mueve de izquierda a derecha de 0 a 100 %.

 No mueva nunca el indicador de progreso hacia atrás durante una operación. La barra debe avanzar constantemente cuando se inicia la operación y alcanzar el 100 % cuando termine. El punto de la barra de progreso es dar al usuario una idea del tiempo que tarda toda la operación, independientemente del número de pasos implicados.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Informes simultáneos (barras de progreso apiladas)
 Si una operación va a tardar mucho tiempo (quizás varios minutos), se pueden usar dos barras de progreso, una que muestra el progreso general de una operación y otra para la progresión del paso actual. Por ejemplo, si un programa de instalación copia muchos archivos, se puede usar una barra de progreso para indicar cuánto tiempo tarda todo el proceso mientras que un segundo puede indicar qué porcentaje del archivo o directorio actual se copia. No notimente más de cinco operaciones o procesos simultáneos mediante barras de progreso apiladas. Si tiene más de cinco operaciones o procesos simultáneos para notificar, use un cuadro de diálogo modal con un botón Cancelar e informe de los detalles de progreso al Ventana de salida.

##### <a name="textual-descriptions"></a>Descripciones textuales
 Use una descripción textual que acompaña a lo que sucede y el tiempo estimado para completarse. Si no es posible determinar cuánto tiempo va a tardar una operación, una mejor opción para proporcionar comentarios podría ser un icono animado en lugar de una barra de progreso.

 Visual Studio proporciona una barra de progreso estándar en la barra de estado que puede usar cualquier producto integrado en Visual Studio. Para obtener descripciones textuales de lo que sucede mientras se anima la barra de progreso, se puede actualizar el texto de la barra de estado.

#### <a name="other-progress-indicators"></a>Otros indicadores de progreso

##### <a name="ants-animated-horizontal-dots"></a>Ants (puntos horizontales animados)
 ![Hormigas de progreso](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Ants", puntos horizontales animados, proporcionan una referencia visual para un proceso de servidor de ida y vuelta indeterminado.

##### <a name="spinner-progress-ring"></a>Spinner (anillo de progreso)
 ![Control giratorio de progreso](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 El indicador de número (también conocido como "anillo de progreso") es un indicador de progreso indeterminado que se usa principalmente en relación con la interfaz de usuario contextual. Mostrar un spinner cerca de su contenido relacionado, como un encabezado de categoría textual, mensajería o control.

##### <a name="cursor-feedback"></a>Comentarios del cursor
 Para las operaciones que tarden entre 2 y 7 segundos, proporcione comentarios sobre el cursor. Normalmente, esto significa usar el cursor de espera proporcionado por el sistema operativo. Para obtener instrucciones, vea el artículo de MSDN [Cursors.Wait (Propiedad).](/dotnet/api/system.windows.input.cursors.wait)

#### <a name="progress-indicator-locations"></a>Ubicaciones de indicadores de progreso

##### <a name="status-bar"></a>Barra de estado
 La barra de estado proporciona a la aplicación un lugar para mostrar mensajes e información útil al usuario sin interrumpir el trabajo del usuario. Normalmente se muestra en la parte inferior de una ventana, el estado del progreso será un panel de información sobre herramientas que incluye un mensaje sobre la medida del progreso en combinación con un indicador de barra de progreso.

 ![Barra de estado con barra de progreso](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **Barra de estado con barra de progreso**

 ![Barra de estado con mensajes](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Barra de estado con descripción textual**

##### <a name="infobar"></a>Barra de información
 De forma similar a la barra de estado, la barra de información proporciona mensajes y notificaciones contextuales, que también se pueden emparejar con indicadores de progreso indeterminados, como la barra de progreso o el indicador de número. La barra de información no debe proporcionar un progreso de nivel granular ni una indicación de progreso determinada. Vea [Barras de información](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![Barra de información con barra y mensajes de progreso](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **Barra de información con barra de progreso y descripción textual**

 ![Barra de información dentro de una ventana](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>En línea
 La indicación de progreso en línea se puede representar mediante cualquiera de los tipos de cargador de progreso. Normalmente, el indicador de progreso se empareja con la mensajería, pero esto no es un requisito.

 ![Control giratorio de progreso en línea](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Spinner combinado con descripción textual**

 ![Barras de progreso apiladas en línea](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Determinación de las barras de progreso apiladas**

 ![Mensajes de progreso en línea](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Explorador de servidores texto en línea: Actualizar...**

##### <a name="tool-windows"></a>Ventanas de herramientas
 La indicación de progreso global se representa mediante una barra de progreso indeterminada que se coloca directamente debajo de la barra de herramientas.

 ![Barra de progreso indeterminada global](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Team Explorer barra de progreso indeterminado global**

##### <a name="dialogs"></a>Cuadros de diálogo
 Los diálogos pueden contener cualquiera de los tipos de cargador de progreso. Los indicadores de progreso se pueden emparejar con la mensajería, así como combinarse con varios niveles de indicación de progreso para representar procesos granulares y sub- .

 ![Cuadro de diálogo con varios tipos de indicador de progreso](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Visual Studio diálogo con procesos simultáneos y varios tipos de indicadores de progreso**

 ![Cuadro de diálogo con cargador y mensajes de progreso](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Visual Studio diálogo con el cargador de progreso y comandos en línea de mensajería**

##### <a name="document-well"></a>Documento completo
 El documento puede mostrar varios tipos de cargador de progreso en combinación con controles.

 ![Mensajes de progreso en la sección de documentos](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Barra de progreso indeterminada debajo de la barra de herramientas**

##### <a name="output-window"></a>Ventana de salida
 La ventana Salida es adecuada para controlar la progresión del proceso y el estado de progreso continuo a través de mensajería textual inserta. Debe usar la barra Estado junto con los informes de progreso de la ventana salida.

 ![Mensajes de progreso en la ventana de salida](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Ventana de salida con el estado del proceso en curso y la mensajería de espera**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Barras de información

### <a name="overview"></a>Información general
 Las barras de información dan al usuario un indicador cerca de su punto de atención y el uso del control de barra de información compartido garantiza la coherencia en la apariencia visual y la interacción.

 ![Barra de información](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Barras de información en Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Usos adecuados para una barra de información

- Para proporcionar al usuario un mensaje sin bloqueo pero importante relevante para el contexto actual

- Para indicar que la interfaz de usuario está en un estado o condición determinados que conlleva algunas implicaciones de interacción, como la depuración histórica

- Para notificar al usuario que el sistema ha detectado problemas, como cuando una extensión está causando problemas de rendimiento

- Para proporcionar al usuario una manera de realizar acciones fácilmente, como cuando el editor detecta que un archivo tiene pestañas y espacios mixtos

##### <a name="do"></a>Sí:

- Mantenga el texto corto del mensaje de la barra de información y hasta el punto.

- Mantenga el texto en vínculos y botones concisa.

- Asegúrese de que las opciones de "acción" que proporcione a los usuarios sean mínimas, mostrando solo las acciones necesarias.

##### <a name="dont"></a>No:

- Use una barra de información para ofrecer comandos estándar que se deben colocar en una barra de herramientas.

- Use una barra de información en lugar de un cuadro de diálogo modal.

- Cree un mensaje flotante fuera de una ventana.

- Use varias barras de información en varias ubicaciones dentro de la misma ventana.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>¿Se pueden mostrar varias barras de información al mismo tiempo?
 Sí, se pueden mostrar varias barras de información al mismo tiempo. Se mostrarán en orden de llegada por orden de llegada, con la primera barra de información en la parte superior y las barras de información adicionales que se muestran a continuación.

 El usuario verá un máximo de tres barras de información a la vez, después de lo cual, si hay más barras de información disponibles, la región de la barra de información se volverá desplazable.

### <a name="creating-an-infobar"></a>Creación de una barra de información
 La barra de información tiene cuatro secciones, de izquierda a derecha:

- **Icono:** Aquí es donde agregaría cualquier icono que le gustaría mostrar para la barra de información, como un icono de advertencia.

- **Texto:** Puede agregar texto para describir el escenario o situación en el que se encuentra el usuario, junto con vínculos dentro del texto, si es necesario. No olvide mantener el texto concisa.

- **Acciones:** Esta sección debe contener vínculos y botones para las acciones que el usuario puede realizar en la barra de información.

- **Botón Cerrar:** La última sección de la derecha puede tener un botón Cerrar.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Creación de una barra de información estándar en código administrado
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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Creación de una barra de información estándar en código nativo
 Implemente la interfaz IVsInfoBar para proporcionar una barra de información a partir de código nativo.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Obtener un elemento UIElement de la barra de información de una barra de información
 La implementación de InfoBarModel o IVsInfoBar son modelos de datos que se deben convertir en uiElement para que se puedan mostrar en la interfaz de usuario. Un UIElement se puede recuperar con el servicio SVsInfoBarUIFactory/IVsInfoBarUIFactory.

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

### <a name="placement"></a>Selección de ubicación
 Las barras de información se pueden mostrar en una o varias de las siguientes ubicaciones:

- Ventanas de herramientas

- Dentro de una pestaña de documento

> [!IMPORTANT]
> Es posible colocar una barra de información para proporcionar un mensaje sobre el contexto global. Esto aparecería entre las barras de herramientas y el documento. Esto no se recomienda porque provoca problemas con el "salto y el desenlazador" del IDE y debe evitarse a menos que sea absolutamente necesario y adecuado.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Colocación de una barra de información en un elemento ToolWindowPane
 El método ToolWindowPane.AddInfoBar(IVsInfoBar) se puede usar para agregar una barra de información a una ventana de herramientas. Esta API puede agregar un IVsInfoBar (del que InfoBarModel es una implementación predeterminada) o un IVsUIElement.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Colocación de una barra de información en un documento o que no es ToolWindowPane
 Para colocar una barra de información en cualquier IVsWindowFrame, use la propiedad VSFPROPID_InfoBarHost para obtener IVsInfoBarHost para el marco y, a continuación, agregue el elemento UIElement de la barra de información.

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
 Para colocar una barra de información en la ventana principal, use el VSSPROPID_MainWindowInfoBarHost del servicio IVsShell para obtener el IVsInfoBarHost de la ventana principal y, a continuación, agregue el elemento UIElement de la barra de información.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>¿Puedo saber cuándo el usuario realiza una acción en mi barra de información?
 Sí, se devolverán todas las acciones de evento al autor de la barra de información. A continuación, es el autor de la barra de información el que debe tomar medidas en el IDE en función de la selección del usuario en la barra de información. Las barras de información se quitarán automáticamente del host en el que se hizo clic en el botón Cerrar, pero se requiere trabajo adicional si es necesario quitar otras barras de información después del cierre. La telemetría también deberá registrarse de forma independiente en cada barra de información.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Recepción de eventos de la barra de información en toolWindowPane
 ToolWindowPane tiene dos eventos para las barras de información. El evento InfoBarClosed se genera cuando se cierra una barra de información en ToolWindowPane. El evento InfoBarActionItemClicked se genera cuando se hace clic en un hipervínculo o un botón dentro de la barra de información.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Recepción de eventos de la barra de información directamente desde UIElement
 IVsInfoBarUIElement.Advise se puede usar para suscribirse a eventos directamente desde uiElement de una barra de información. La implementación de IVsInfoBarUIEvents permitirá al autor recibir eventos de cierre y clic.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> Validación de errores
 Cuando un usuario escribe información que no es aceptable, como cuando se omite un campo obligatorio o cuando los datos se escriben en un formato incorrecto, es mejor usar la validación del control o los comentarios cerca del control en lugar de usar un cuadro de diálogo de error emergente de bloqueo.

### <a name="field-validation"></a>Validación de campos
 La validación de formularios y campos consta de tres componentes: un control, un icono y una información sobre herramientas. Aunque varios tipos de controles pueden usar esto, se usará un cuadro de texto como ejemplo.

 ![Validación de campos &#40;en blanco&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Si el campo es necesario, debe haber texto de marca de agua que indique y el fondo del campo debe ser amarillo claro (VSColor: ) y el primer plano debe **\<Required>** `Environment.ControlEditRequiredBackground` ser gris (VSColor: `Environment.ControlEditRequiredHintText` ):

 ![Validación de campo con la etiqueta "Obligatorio"](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 El programa puede determinar que el  control está en un estado de contenido no válido especificado cuando el foco se mueve a otro control o cuando el usuario hace clic en un botón de confirmación [Aceptar] o cuando el usuario guarda el documento o el formulario.

 Cuando se determina el estado de contenido no válido, aparece un icono dentro del control o justo al lado de él. La información sobre herramientas que describe el error debe aparecer al mantener el puntero sobre el icono o el control. Además, debe aparecer un borde de 1 píxel alrededor del control que crea el estado no válido.

 ![Especificaciones de diseño de validación de campo](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Especificaciones de diseño para la validación de campos**

#### <a name="acceptable-variations-for-icon-location"></a>Variaciones aceptables para la ubicación del icono
 Hay incontables casos únicos en los que los usuarios deben estar informados sobre los errores de validación. Teniendo en cuenta el tipo de control y la configuración de la interfaz de usuario, elija la ubicación del icono adecuada para su situación.

 ![Ubicaciones aceptables para la ubicación del icono](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Variaciones aceptables para ubicaciones de icono de validación de campos**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Validación que requiere un recorrido de ida y vuelta a un servidor o una conexión de red
 En algunos casos, se requiere un recorrido de ida y vuelta al servidor para comprobar el contenido y sería importante mostrar el progreso del usuario, la comprobación y los estados de error. En la ilustración siguiente se muestra un ejemplo de este caso y la interfaz de usuario recomendada.

 ![Validación que implica un viaje de ida y vuelta a un servidor](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Validación que implica un viaje de ida y vuelta a un servidor**

 Tenga en cuenta que se debe proporcionar el espacio disponible adecuado a la derecha del control para dar cabida a la "Comprobación...". y texto "Reintentar".

#### <a name="in-place-warning-text"></a>Texto de advertencia en el lugar
 Cuando hay espacio disponible para colocar el mensaje de error cerca del control en un estado de error, es preferible usar solo la información sobre herramientas.

 ![En&#45;advertencia](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Texto de advertencia en el lugar**

#### <a name="watermarks"></a>Marcas de agua
 A veces, todo un control o ventana se encuentra en un estado de error. En esta situación, use una marca de agua para indicar el error.

 ![Marca de agua](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Validación de campos de marca de agua**
