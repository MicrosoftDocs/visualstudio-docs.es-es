---
title: Ejecutar aplicaciones de Windows Phone en el emulador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5027c9d40d37aeaee6186662567a009fb051900e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812615"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Ejecutar aplicaciones de Windows Phone en el simulador 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El emulador de Windows Phone proporciona un entorno virtual en el que puede depurar y probar aplicaciones de Windows Phone en el equipo sin un dispositivo físico. Puede simular eventos táctiles y rotaciones, y elegir el tamaño y la resolución de la pantalla física que desee emular. También puede probar muchas características usadas habitualmente como, por ejemplo, la ubicación, las redes, las notificaciones, los sensores, el acelerómetro y la tarjeta SD opcional.  
  
 Para obtener más información sobre las características que puede probar en el emulador, consulte [probar características de la aplicación en el emulador de Windows Phone](http://msdn.microsoft.com/en-us/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Junto con Visual Studio, el emulador proporciona un entorno completo donde puede diseñar, desarrollar, depurar y probar aplicaciones de Windows Phone.  
  
##  <a name="BKMK_run"></a> Ejecutar una aplicación de Windows Phone en el emulador  
 Al desarrollar una aplicación de Windows Phone, puede usar Windows Phone Emulator para implementar y probar la aplicación rápidamente. Sin embargo, le recomendamos que pruebe la aplicación en un dispositivo Windows Phone antes de publicarla en la Tienda de Windows Phone. De este modo, podrá experimentar la aplicación tal como la experimentarán los usuarios.  
  
 Al ejecutar una aplicación de Windows Phone por primera vez en Windows Phone Emulator, tienen lugar los siguientes eventos:  
  
1. El emulador se inicia.  
  
2. El emulador carga el sistema operativo de Windows Phone.  
  
3. El emulador muestra la pantalla Inicio de Windows Phone.  
  
4. La aplicación se implementa en el emulador.  
  
5. La aplicación se ejecuta en el emulador.  
  
   Si el emulador seleccionado ya se está ejecutando, la aplicación se implementa y se inicia en el emulador en ejecución. Solo se puede ejecutar una instancia de cada emulador a la vez.  
  
> [!TIP]
>  Al probar una aplicación en el emulador, deja el emulador abierto entre cada sesión de depuración para poder ejecutar la aplicación de nuevo rápidamente.  
  
###  <a name="BKMK_vs"></a> Ejecutar una aplicación desde Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>Para implementar y ejecutar una aplicación desde Visual Studio  
  
1.  En Visual Studio, abra un proyecto de Windows Phone.  
  
2.  En el **estándar** barra de herramientas, seleccione una de las opciones del emulador.  
  
     ![Lista de imágenes del emulador de Windows Phone](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3.  Para implementar y ejecutar la aplicación con la depuración, en el **depurar** menú, haga clic en **Iniciar depuración**, o presione F5.  
  
     Para implementar y ejecutar la aplicación sin depuración, en el **depurar** menú, haga clic en **iniciar sin depurar**, o presione Ctrl + F5.  
  
     La aplicación se ha implementado y se ha iniciado.  
  
     Para implementar la aplicación sin ejecutarla, en el **compilar** menú, haga clic en **implementar solución**.  
  
##### <a name="to-stop-a-running-app"></a>Para detener una aplicación en ejecución  
  
- Para detener una aplicación en ejecución, realice una de las siguientes operaciones:  
  
  - En Visual Studio, en el **depurar** menú, haga clic en **Detener depuración**, o bien presione MAYÚS+F5.  
  
  - En el emulador, presione el **volver** botón Salir de la aplicación. Si la página activa de la aplicación no era una página de inicio de la aplicación, es posible que deba presionar el **volver** botón más de una vez.  
  
    La aplicación se cierra y se abre la pantalla Inicio. Esta operación finaliza la sesión de depuración actual.  
  
##### <a name="to-restart-an-app-without-debugging"></a>Para reiniciar una aplicación sin depuración  
  
1.  En el emulador, en la pantalla Inicio, deslice el dedo rápidamente hacia la izquierda para ver la lista de aplicaciones.  
  
2.  En la lista de aplicaciones, pulse el icono de la aplicación. La aplicación se reinicia sin depuración.  
  
##### <a name="to-deactivate-a-running-app"></a>Para desactivar una aplicación en ejecución  
  
1.  Antes de ejecutar la aplicación, en Visual Studio, haga clic en el proyecto en el Explorador de soluciones y, a continuación, seleccione **propiedades** para abrir **Diseñador de proyectos**.  
  
2.  En **Diseñador de proyectos**, en el **depurar** página, deje el **marcador de exclusión tras desactivación durante la depuración** casilla desactivada si desea que la aplicación entre en un inactivas estado cuando desactivado. Active la casilla si quiere que se asigne a la aplicación un marcador de exclusión al desactivarla.  
  
3.  En el **depurar** menú, haga clic en **Iniciar depuración**, o presione F5 para ejecutar la aplicación.  
  
4.  En el emulador, presione el **iniciar** botón. Aparece la pantalla Inicio y se desactiva la aplicación. La aplicación entra en estado inactivo o está extinguiendo, según la configuración de la **marcador de exclusión tras desactivación durante la depuración** casilla de verificación.  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Para reactivar una aplicación inactiva o con marcador de exclusión  
  
-   En el emulador, presione el **volver** botón para volver a la aplicación. Si navega a otras páginas o ha abierto otra aplicación, es posible que deba presionar el **volver** botón más de una vez para reactivar la aplicación.  
  
     Se reanudará la sesión de depuración. Si el depurador se ha desasociado de la aplicación, es posible que deba presionar F5 para reanudar la sesión de depuración.  
  
###  <a name="BKMK_depltool"></a> Ejecutar una aplicación con la herramienta de implementación de aplicaciones  
 También puede usar la herramienta de implementación de aplicaciones de Windows Phone (**AppDeploy.exe**) para ejecutar la aplicación en el emulador. Esta herramienta es una aplicación independiente que se instala al instalar las herramientas de desarrollo de Windows Phone.  
  
 Para obtener más información, consulte [aplicaciones de implementación de Windows Phone 8.1 con la herramienta de implementación de aplicaciones](http://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
##  <a name="BKMK_toolbar"></a> Configurar el emulador de Windows Phone con la barra de herramientas del emulador  
 En esta table se muestran los botones de configuración disponibles en la barra de herramientas del emulador.  
  
|Botones de barra de herramientas|Opciones de configuración|  
|---------------------|---------------------------|  
|![Las opciones en la barra de herramientas del emulador de Windows Phone de entrada](../debugger/media/wp-emulator.png "WP_Emulator_")|**Configurar entrada único punto o multipunto**<br /><br /> Al habilitar una entrada de multipunto, puede hacer clic con el botón derecho para mover los puntos táctiles sin tocar la pantalla. A continuación, puedeshacer clic con el botón izquierdo para mover ambos puntos táctiles simultáneamente.|  
|![Orientación de la barra de herramientas del emulador de Windows Phone](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Configurar la orientación del emulador**<br /><br /> Puede cambiar la orientación en Windows Phone Emulator por una de las tres orientaciones posibles: vertical, horizontal a la izquierda u horizontal a la derecha. El tamaño del emulador no cambia al cambiar la orientación.<br /><br /> Para cambiar la orientación, haga clic en el **Girar a la izquierda** botón o la **Girar a la derecha** botón.|  
|![Cambiar el tamaño de las opciones en la barra de herramientas del emulador de Windows Phone](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Configurar el tamaño del emulador**<br /><br /> Puede cambiar el tamaño del emulador en la pantalla del equipo host. Los puntos por pulgada (PPP) del emulador se basan en los PPP del monitor host, independientemente del valor del zoom.<br /><br /> -Para ajustar el emulador a la pantalla, haga clic en el **ajustar a la pantalla** botón.<br />-Para cambiar la configuración del zoom, haga clic en el **Zoom** botón. El **Zoom** abre el cuadro de diálogo. En el **Zoom** diálogo cuadro, escriba un valor de zoom entre 33 y 100.|  
  
##  <a name="BKMK_buttons"></a> Utilice los botones de hardware simulados en el emulador  
 Simula el uso de los botones de hardware de un teléfono mediante los botones de hardware simulados situados a la derecha de la pantalla del emulador.  
  
- Haga clic en el **Power** botón para simular la activación y desactivación la presentación. Haga clic y mantenga presionado para simular la activación y desactivación del teléfono.  
  
- Haga clic en el **Subir volumen** o **Bajar volumen** botón para simular el cambio de volumen del altavoz del teléfono para llamadas telefónicas y notificaciones.  
  
- El **cámara** botón inicia la aplicación de cámara. Puede simular cómo hacer una foto o grabar un vídeo mediante los controles de la aplicación de la cámara.  
  
  La siguiente captura de pantalla muestra los botones de hardware simulados.  
  
1. La imagen de la izquierda muestra la pantalla Inicio del emulador.  
  
2. Imagen del centro muestra el emulador tras pulsar el **Power** botón para apagar la pantalla.  
  
3. La imagen de la derecha muestra la pantalla del emulador tras pulsar el **Subir volumen** para aumentar el volumen.  
  
   ![Los botones en el emulador de Windows Phone](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
##  <a name="BKMK_tasks_kbd"></a> Usar el teclado del equipo con el emulador  
 El emulador admite la asignación del teclado de hardware del equipo de desarrollo al teclado de un Windows Phone. El comportamiento de las teclas es el mismo que en un dispositivo Windows Phone.  
  
 De forma predeterminada, el teclado de hardware no está habilitado. Esta implementación es equivalente a un teclado deslizante que debe implementarse antes de su uso. Antes de habilitar el teclado de hardware, el emulador acepta la entrada de teclas solo desde las teclas de control.  
  
 El emulador no admite caracteres especiales del teclado de una versión localizada de un equipo de desarrollo de Windows. Para escribir caracteres especiales que están presentes en un teclado localizado, use el Panel de entrada de software (SIP).  
  
 Para utilizar el teclado de su equipo en el emulador, presione la tecla RE PÁG o la tecla PAUSA/INTERRUMPIR (emulador de Windows 8/8.1), o bien la tecla F4 (emulador Windows 10).  
  
 Para dejar de utilizar el teclado de su equipo en el emulador, presione la tecla AV PÁG o la tecla PAUSA/INTERRUMPIR (emulador de Windows 8/8.1), o bien la tecla F4 (emulador Windows 10).  
  
 La tabla siguiente indica las teclas de un teclado de hardware que puede usar para emular los botones y otros controles en Windows Phone.  
  
|Tecla de hardware del equipo|Botón de hardware de Windows Phone|Notas|  
|---------------------------|-----------------------------------|-----------|  
|F1|ATRÁS|Las pulsaciones prolongadas funcionan según lo previsto.|  
|F2|INICIO|Las pulsaciones prolongadas funcionan según lo previsto.|  
|F3|BUSCAR||  
|F4|En el emulador de Windows 10, alterna entre utilizar el teclado del equipo local y no usarlo.|No es aplicable en el emulador de Windows 8/8.1.|  
|F5|No es aplicable.||  
|F6|CÁMARA A LA MITAD|Un botón de cámara dedicado que se presiona hasta la mitad.|  
|F7|CÁMARA COMPLETO|Un botón de cámara dedicado.|  
|F8|No es aplicable.||  
|F9|SUBIR VOLUMEN||  
|F10|BAJAR VOLUMEN||  
|F11|No es aplicable.||  
|F12|INICIO/APAGADO|Presione la tecla F12 dos veces para habilitar la pantalla de bloqueo.<br /><br /> Las pulsaciones prolongadas funcionan según lo previsto.|  
|ESC|ATRÁS|Las pulsaciones prolongadas funcionan según lo previsto.|  
|PAUSA/INTERRUMPIR|Alternar teclado (solo en el emulador Windows 8/8.1).|No es aplicable en el emulador de Windows 10.|  
|RE PÁG|Activa el teclado de hardware (solo en Windows 8/8.1 emulador).|No es aplicable en el emulador de Windows 10.|  
|AV PÁG|Desactiva el teclado de hardware (solo en Windows 8/8.1 emulador).|No es aplicable en el emulador de Windows 10.|  
  
##  <a name="BKMK_checkpoints"></a> Guardar y cargar puntos de control personalizados  
 Guardar una instantánea del estado del emulador mediante la **puntos de control** pestaña el emulador de **herramientas adicionales**. Esta característica es útil si prueba a menudo su aplicación con los mismos datos y la misma configuración.  
  
 Por ejemplo, si la aplicación necesita varios contactos, puede crear los registros de contactos una vez y guardar una instantánea del emulador. De lo contrario, deberá recrear los registros de contactos cada vez que inicie el emulador.  
  
- Haga clic en **nuevo punto de control** para capturar una nueva instantánea del estado del emulador con los datos y la configuración necesaria para probar la aplicación de nuevo más tarde. El nuevo punto de control se agrega a la **puntos de control** lista.  
  
   Puede capturar un punto de control mientras el depurador esté asociado al emulador.  
  
- Seleccione un punto de control en el **puntos de control** lista para ver la información sobre el punto de control.  
  
- Seleccione el botón de radio en el **predeterminada** columna para que el punto de control predeterminado de un punto de control para el emulador activo.  
  
- Haga clic en **restaurar** para reiniciar el sistema operativo de Windows Phone en el emulador y cargar la instantánea seleccionada.  
  
- Haga clic en **eliminar** para eliminar una instantánea que ya no necesite.  
  
  La imagen del emulador original aparece siempre como el primer elemento de la **puntos de control** lista y que no se puede cambiar ni eliminar. Sin embargo, puede seleccionar una instantánea diferente como imagen del emulador predeterminada.  
  
  ![Pestaña de puntos de control del emulador de Windows Phone](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
##  <a name="BKMK_tasks_shot"></a> Realizar capturas de pantalla en el emulador  
 Puede crear capturas de pantalla de sus aplicaciones de Windows Phone mediante la herramienta de captura de pantallas desde la ventana Herramientas adicionales. La herramienta crea archivos PNG que coinciden con la resolución del emulador en ejecución.  
  
 ![Capturas de pantalla desde el Windows Phone Emulator](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Para crear una captura de pantalla de una aplicación mediante la herramienta integrada de captura de pantallas del emulador  
  
1. Para optimizar la calidad de las capturas de pantalla, establezca el nivel de zoom del emulador al 100 por ciento. Cuando más elevado sea el nivel de zoom, mejor será la calidad de la captura de pantalla.  
  
2. Iniciar la aplicación en el emulador.  
  
3. En la barra de herramientas del emulador, haga clic en el botón de expansión para abrir la **herramientas adicionales** ventana.  
  
4. Haga clic en el **captura de pantalla** ficha.  
  
5. Cuando la aplicación está lista, haga clic en el **capturar** botón.  
  
    La captura de pantalla aparecerá en el área de trabajo.  
  
6. Haga clic en el **guardar** botón para abrir el **Guardar como** cuadro de diálogo.  
  
7. Elija la ubicación y **nombre de archivo** que desee y, a continuación, haga clic en **guardar**.  
  
8. También tiene la opción de navegar a otras páginas de la aplicación y realizar capturas de pantalla adicionales.  
  
9. Inicie un emulador con una resolución de pantalla diferente para realizar las mismas capturas de pantalla en otra resolución. Si ejecutó la aplicación con depuración, debe detener la depuración para poder volver a ejecutarla en otro emulador.  
  
   Deshabilite los contadores de velocidad de fotogramas en la pantalla del emulador antes de realizar capturas de pantalla que se enviarán a la Tienda de Windows Phone.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Para deshabilitar los contadores de velocidad de fotogramas en el emulador antes de realizar capturas de pantalla  
  
-   Especifique una compilación de versión en Visual Studio. Después de especificar una versión de lanzamiento, inicie la aplicación seleccionando el **implementar _[nombre de la aplicación]_**  vincular en el **compilar** menú.  
  
-   Como alternativa, puede convertir en comentario la línea de código en el archivo app.xaml.cs o app.xaml.vb que establece el valor de `EnableFrameRateCounter` como `true`.



