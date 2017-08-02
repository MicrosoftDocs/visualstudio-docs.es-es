---
title: "Ejecutar aplicaciones de Windows Phone en el simulador  | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ejecutar aplicaciones de Windows Phone en el simulador 
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Se aplica solo a Windows Phone](~/docs/debugger/media/phone_only_content.png "phone\_only\_content")  
  
 El emulador de Windows Phone es una aplicación de escritorio que simula un Windows Phone. El emulador proporciona un entorno virtualizado en el que puede depurar y probar aplicaciones de Windows Phone en el equipo sin un dispositivo físico. Puede simular eventos táctiles y rotaciones, y elegir el tamaño y la resolución de la pantalla física que desee emular. También puede probar muchas características usadas habitualmente como, por ejemplo, la ubicación, las redes, las notificaciones, los sensores, el acelerómetro y la tarjeta SD opcional.  
  
 Para obtener más información sobre las características que puede probar en el emulador, consulte [Probar las características de la aplicación en el emulador de Windows Phone](http://msdn.microsoft.com/es-es/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Junto con Visual Studio, el emulador proporciona un entorno completo donde puede diseñar, desarrollar, depurar y probar aplicaciones de Windows Phone.  
  
## En este tema  
  
-   [Ejecutar una aplicación de Windows Phone en el emulador](#BKMK_run)  
  
    -   [Ejecutar una aplicación desde Visual Studio](#BKMK_vs)  
  
    -   [Ejecutar una aplicación con la herramienta Implementación de aplicación](#BKMK_depltool)  
  
-   [Configurar el emulador de Windows Phone con la barra de herramientas del emulador](#BKMK_toolbar)  
  
-   [Usar los botones de hardware simulados en el emulador](#BKMK_buttons)  
  
-   [Usar el teclado del equipo con el emulador](#BKMK_tasks_kbd)  
  
-   [Guardar y cargar puntos de control personalizados](#BKMK_checkpoints)  
  
-   [Realizar capturas de pantalla en el emulador](#BKMK_tasks_shot)  
  
##  <a name="BKMK_run"></a> Ejecutar una aplicación de Windows Phone en el emulador  
 Al desarrollar una aplicación de Windows Phone, puede usar Windows Phone Emulator para implementar y probar la aplicación rápidamente. Sin embargo, le recomendamos que pruebe la aplicación en un dispositivo Windows Phone antes de publicarla en la Tienda de Windows Phone. De este modo, podrá experimentar la aplicación tal como la experimentarán los usuarios.  
  
 Al ejecutar una aplicación de Windows Phone por primera vez en el emulador de Windows Phone, ocurre lo siguiente:  
  
1.  El emulador se inicia.  
  
2.  El emulador carga el sistema operativo de Windows Phone.  
  
3.  El emulador muestra la pantalla Inicio de Windows Phone.  
  
4.  La aplicación se implementa en el emulador.  
  
5.  La aplicación se ejecuta en el emulador.  
  
 Si el emulador seleccionado ya se está ejecutando, la aplicación se implementa y se inicia en el emulador en ejecución. Solo se puede ejecutar una instancia de cada emulador a la vez.  
  
> [!TIP]
>  Al probar una aplicación en el emulador, deje el emulador abierto entre cada sesión de depuración para poder ejecutar la aplicación de nuevo rápidamente.  
  
###  <a name="BKMK_vs"></a> Ejecutar una aplicación desde Visual Studio  
  
##### Para implementar y ejecutar una aplicación desde Visual Studio  
  
1.  En Visual Studio, abra un proyecto de Windows Phone.  
  
2.  En la barra de herramientas **Estándar**, seleccione una de las opciones del emulador.  
  
     ![Lista de imágenes del Emulador de Windows Phone](~/docs/debugger/media/wp_emulator_list.png "WP\_Emulator\_list")  
  
3.  Para implementar y ejecutar la aplicación con la depuración, en el menú **Depurar**, haga clic en **Iniciar depuración** o presione F5.  
  
     Para implementar y ejecutar la aplicación sin depurar, en el menú **Depurar**, haga clic en **Iniciar sin depurar** o presione Ctrl\+F5.  
  
     La aplicación se implementa e inicia.  
  
     Para implementar la aplicación sin ejecutarla, en el menú **Compilar**, haga clic en **Implementar solución**.  
  
##### Para detener una aplicación en ejecución  
  
-   Para detener una aplicación en ejecución, realice una de las siguientes operaciones:  
  
    -   En Visual Studio, en el menú **Depurar**, haga clic en **Detener depuración** o presione Mayús\+F5.  
  
    -   En el emulador, presione el botón **Atrás** para salir de la aplicación. Si la página activa de la aplicación no era una página de inicio de la aplicación, es posible que deba presionar el botón **Atrás** más de una vez.  
  
     La aplicación se cierra y se abre la pantalla Inicio. Esta operación finaliza la sesión de depuración actual.  
  
##### Para reiniciar una aplicación sin depuración  
  
1.  En el emulador, en la pantalla Inicio, deslice el dedo rápidamente hacia la izquierda para ver la lista de aplicaciones.  
  
2.  En la lista de aplicaciones, pulse el icono de la aplicación. La aplicación se reinicia sin depuración.  
  
##### Para desactivar una aplicación en ejecución  
  
1.  Antes de ejecutar la aplicación, en Visual Studio, haga clic con el botón secundario en el proyecto en el Explorador de soluciones y seleccione **Propiedades** para abrir **Diseñador de proyectos**.  
  
2.  En **Diseñador de proyectos**, en la página **Depurar**, deje la casilla **Marcador de exclusión tras desactivación durante la depuración** desactivada si quiere que la aplicación entre en estado inactivo al desactivarla. Active la casilla si quiere que se asigne a la aplicación un marcador de exclusión al desactivarla.  
  
3.  En el menú **Depurar**, haga clic en **Iniciar depuración** o presione F5 para ejecutar la aplicación.  
  
4.  En el emulador, presione el botón **Iniciar**. Aparece la pantalla Inicio y se desactiva la aplicación. La aplicación entra en estado inactivo o se le asigna un marcador de exclusión, dependiendo de la configuración de la casilla **Marcador de exclusión tras la desactivación durante la depuración**.  
  
##### Para reactivar una aplicación inactiva o con marcador de exclusión  
  
-   En el emulador, presione el botón **Atrás** para volver a la aplicación. Si navega a otras páginas o ha abierto otra aplicación, es posible que deba presionar el botón **Atrás** más de una vez para reactivar la aplicación.  
  
     La sesión de depuración se reanuda. Si el depurador se ha desasociado de la aplicación, es posible que deba presionar F5 para reanudar la sesión de depuración.  
  
###  <a name="BKMK_depltool"></a> Ejecutar una aplicación con la herramienta Implementación de aplicación  
 También puede usar la herramienta Implementación de aplicación de Windows Phone \(**AppDeploy.exe**\) para ejecutar la aplicación en el emulador. Esta herramienta es una aplicación independiente que se instala al instalar las herramientas de desarrollo de Windows Phone.  
  
 Para obtener más información, consulte [Implementar aplicaciones de Windows Phone 8.1 con la herramienta Implementación de aplicaciones](../Topic/Deploy%20Windows%20Phone%208.1%20apps%20with%20the%20Application%20Deployment%20tool.md).  
  
##  <a name="BKMK_toolbar"></a> Configurar el emulador de Windows Phone con la barra de herramientas del emulador  
 En la siguiente captura de pantalla se muestran los botones de configuración disponibles en la barra de herramientas del emulador.  
  
 f21574ab-5970-4b7a-9281-c13073bf6767  
  
|Botones de barra de herramientas|Opciones de configuración|  
|--------------------------------------|-------------------------------|  
|![Opciones de entrada en la barra de herramientas del Emulador de Windows Phone](~/docs/debugger/media/wp_emulator_.png "WP\_Emulator\_")|**Configurar entrada único punto o multipunto**<br /><br /> Al habilitar la entrada de multipunto, puede hacer clic con el botón secundario para mover los puntos táctiles sin tocar la pantalla. A continuación, puede hacer clic con el botón izquierdo para mover ambos puntos táctiles simultáneamente.|  
|![Orientación en la barra de herramientas del Emulador de Windows Phone](~/docs/debugger/media/wp_emulator_rotation.png "WP\_Emulator\_rotation")|**Configurar la orientación del emulador**<br /><br /> Puede cambiar la orientación en Windows Phone Emulator por una de las tres orientaciones posibles: vertical, horizontal a la izquierda u horizontal a la derecha. El tamaño del emulador no cambia al cambiar la orientación.<br /><br /> Para cambiar la orientación, haga clic en los botones **Girar a la izquierda** o **Girar a la derecha**.|  
|![Opciones de tamaño en la barra de herramientas del Emulador de Windows Phone](~/docs/debugger/media/wp_emulator_size.png "WP\_Emulator\_size")|**Configurar el tamaño del emulador**<br /><br /> Puede cambiar el tamaño del emulador en la pantalla del equipo host. Los puntos por pulgada \(PPP\) del emulador se basan en los PPP del monitor host, independientemente del valor del zoom.<br /><br /> -   Para ajustar el emulador a la pantalla, haga clic en el botón **Ajustar a la pantalla**.<br />-   Para cambiar la configuración del zoom, haga clic en el botón **Zoom**. Se abrirá el cuadro de diálogo **Zoom**. En el cuadro de diálogo **Zoom**, escriba un valor de zoom entre 33 y 100.|  
  
##  <a name="BKMK_buttons"></a> Usar los botones de hardware simulados en el emulador  
 Simule el uso de los botones de hardware de un teléfono con los botones de hardware simulados situados a la derecha de la pantalla del emulador.  
  
-   Haga clic en el botón **inicio\/apagado** para simular la activación y desactivación del dispositivo. Haga clic y mantenga presionado para simular la activación y desactivación del teléfono.  
  
-   Haga clic en los botones **Subir volumen** o **Bajar volumen** para simular el cambio de volumen del altavoz del teléfono para llamadas telefónicas y notificaciones.  
  
-   El botón **Cámara** inicia la aplicación de cámara. Puede simular cómo hacer una foto o grabar un vídeo con los controles de la aplicación de la cámara.  
  
 La siguiente captura de pantalla muestra los botones de hardware simulados.  
  
1.  La imagen de la izquierda muestra la pantalla Inicio del emulador.  
  
2.  La imagen del centro muestra el emulador tras pulsar el botón **inicio\/apagado** para apagar la pantalla.  
  
3.  La imagen de la derecha muestra la pantalla del emulador tras pulsar el botón **Subir volumen** para aumentar el volumen.  
  
 ![Botones del Emulador de Windows Phone](~/docs/debugger/media/wp_emulator_buttons.png "WP\_Emulator\_buttons")  
  
##  <a name="BKMK_tasks_kbd"></a> Usar el teclado del equipo con el emulador  
 El emulador admite la asignación del teclado de hardware del equipo de desarrollo al teclado de un Windows Phone. El comportamiento de las teclas es el mismo que en un dispositivo Windows Phone.  
  
 De forma predeterminada, el teclado de hardware no está habilitado. Esta implementación es equivalente a un teclado deslizante que debe implementarse antes de su uso. Antes de habilitar el teclado de hardware, el emulador acepta la entrada de teclas solo desde las teclas de control.  
  
 El emulador no admite caracteres especiales del teclado de una versión localizada de un equipo de desarrollo de Windows. Para escribir caracteres especiales que están presentes en un teclado localizado, use el Panel de entrada de software \(SIP\).  
  
#### Para usar el teclado del equipo en el emulador  
  
-   Presione la tecla RE PÁG.  
  
     \- or \-  
  
-   Presione la tecla PAUSA\/INTERRUMPIR.  
  
#### Para dejar de usar el teclado de su equipo y usar el teclado de hardware del emulador  
  
-   Presione la tecla AV PÁG.  
  
     \- or \-  
  
-   Presione la tecla PAUSA\/INTERRUMPIR.  
  
 La tabla siguiente indica las teclas de un teclado de hardware que puede usar para emular los botones y otros controles en Windows Phone.  
  
|Tecla de hardware del equipo|Botón de hardware de Windows Phone|Notas|  
|----------------------------------|----------------------------------------|-----------|  
|F1|ATRÁS|Las pulsaciones prolongadas funcionan según lo esperado.|  
|F2|INICIO|Las pulsaciones prolongadas funcionan según lo esperado.|  
|F3|BÚSQUEDA||  
|F4|No disponible.||  
|F5|No disponible.||  
|F6|CÁMARA A LA MITAD|Un botón de cámara dedicado que se presiona hasta la mitad.|  
|F7|CÁMARA COMPLETO|Un botón de cámara dedicado.|  
|F8|No disponible.||  
|F9|SUBIR VOLUMEN||  
|F10|BAJAR VOLUMEN||  
|F11|No disponible.||  
|F12|INICIO\/APAGADO|Presione la tecla F12 dos veces para habilitar la pantalla de bloqueo.<br /><br /> Las pulsaciones prolongadas funcionan según lo previsto.|  
|ESC|ATRÁS|Las pulsaciones prolongadas funcionan según lo esperado.|  
|PAUSA\/INTERRUMPIR|Alternar teclado|Activa o desactiva el teclado de hardware.|  
|RE PÁG|Teclado arriba|Activa el teclado de hardware.|  
|AV PÁG|Teclado abajo|Desactiva el teclado de hardware.|  
  
##  <a name="BKMK_checkpoints"></a> Guardar y cargar puntos de control personalizados  
 Guarde una instantánea del estado del emulador mediante la pestaña **Puntos de control** de las **Herramientas adicionales** del emulador. Esta característica es útil si prueba a menudo su aplicación con los mismos datos y la misma configuración.  
  
 Por ejemplo, si la aplicación necesita varios contactos, puede crear los registros de contactos una vez y guardar una instantánea del emulador. De lo contrario, deberá recrear los registros de contactos cada vez que inicie el emulador.  
  
-   Haga clic en **Nuevo punto de control** para capturar una nueva instantánea del estado del emulador con los datos y la configuración necesarios para volver a probar la aplicación más adelante. El nuevo punto de control se agrega a la lista **Puntos de control**.  
  
     No puede capturar un punto de control mientras el depurador esté adjunto al emulador.  
  
-   Seleccione un punto de control en el lista **Puntos de control** para ver la información sobre el punto de control.  
  
-   Seleccione el botón de radio en la columna **Predeterminado** para convertir un punto de control en el punto de control predeterminado para el emulador activo.  
  
-   Haga clic en **Restaurar** para reiniciar el sistema operativo de Windows Phone en el emulador y cargar la instantánea seleccionada.  
  
-   Haga clic en **Eliminar** para eliminar una instantánea que ya no necesite.  
  
 La imagen del emulador original aparece siempre como el primer elemento de la lista **Puntos de control** y no se puede cambiar ni eliminar. Sin embargo, puede seleccionar una instantánea diferente como imagen del emulador predeterminada.  
  
 ![Pestaña de puntos de comprobación del Emulador de Windows Phone](~/docs/debugger/media/wp_emulator_checkpoints.png "WP\_Emulator\_checkpoints")  
  
##  <a name="BKMK_tasks_shot"></a> Realizar capturas de pantalla en el emulador  
 Puede crear capturas de pantalla de sus aplicaciones de Windows Phone mediante la herramienta de captura de pantallas desde la ventana Herramientas adicionales. La herramienta crea archivos PNG que coinciden con la resolución del emulador en ejecución.  
  
 ![Capturas de pantalla desde el Emulador de Windows Phone](~/docs/debugger/media/wp_emulator_screenshots.png "WP\_Emulator\_screenshots")  
  
#### Para crear una captura de pantalla de una aplicación mediante la herramienta integrada de captura de pantallas del emulador  
  
1.  Para optimizar la calidad de las capturas de pantalla, establezca el nivel de zoom del emulador al 100 por ciento. Cuanto más elevado sea el nivel de zoom, mejor será la calidad de la captura de pantalla.  
  
2.  Iniciar la aplicación en el emulador.  
  
3.  En la barra de herramientas del emulador, haga clic en el botón de expandir para abrir la ventana **Herramientas adicionales**.  
  
4.  Haga clic en la pestaña **Captura de pantalla de**.  
  
5.  Cuando la aplicación esté lista, haga clic en el botón **Capturar**.  
  
     La captura de pantalla aparecerá en el área de trabajo.  
  
6.  Haga clic en el botón **Guardar** para abrir el cuadro de diálogo **Guardar como**.  
  
7.  Elija la ubicación y el **Nombre de archivo** que quiera y haga clic en **Guardar**.  
  
8.  También tiene la opción de navegar a otras páginas de la aplicación y realizar capturas de pantalla adicionales.  
  
9. Inicie un emulador con una resolución de pantalla diferente para realizar las mismas capturas de pantalla en otra resolución. Si ejecutó la aplicación con depuración, debe detener la depuración para poder volver a ejecutarla en otro emulador.  
  
 Deshabilite los contadores de velocidad de fotogramas en la pantalla del emulador antes de realizar capturas de pantalla que se enviarán a la Tienda de Windows Phone.  
  
#### Para deshabilitar los contadores de velocidad de fotogramas en el emulador antes de realizar capturas de pantalla  
  
-   Especifique una compilación de versión en Visual Studio. Después de especificar una compilación de versión, inicie la aplicación seleccionando el vínculo **Implementar *\[nombre de la aplicación\]*** del menú **Compilar**.  
  
-   Como alternativa, puede convertir en comentario la línea de código en el archivo app.xaml.cs o app.xaml.vb que establece el valor de `EnableFrameRateCounter` en `true`.