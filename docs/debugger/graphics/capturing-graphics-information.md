---
title: Capturar información de gráficos | Documentos de Microsoft
ms.custom: ''
ms.date: 02/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e00dd4d0fae184f092efabb5df4a4f27e76a653a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478098"
---
# <a name="capturing-graphics-information"></a>Capturar información de gráficos
Capture información de gráficos desde la aplicación basada en Direct3D para que pueda usar el Analizador de gráficos de Visual Studio con el fin de diagnosticar problemas de representación y de rendimiento.  
  
## <a name="capturing-graphics-information"></a>Capturar información de gráficos  
 La captura de información de gráficos es un proceso de dos pasos. En primer lugar, ejecute la aplicación en Diagnóstico de gráficos y después especifique uno o varios fotogramas de los que desea capturar información detallada.  
  
### <a name="to-run-your-app-under-graphics-diagnostics"></a>Para ejecutar la aplicación en Diagnóstico de gráficos  
  
-   En la barra de menús, elija **depurar**, **gráficos**, **iniciar la depuración de gráficos**. (Teclado: presione Alt+F5)  
  
-   En el **gráficos** barra de herramientas, elija la **iniciar la depuración de gráficos** botón.  
  
 Mientras se ejecuta una aplicación en Diagnóstico de gráficos, parte de la información de los gráficos se captura en todo momento; entre esta información se incluye la configuración del dispositivo, la creación de la cadena de intercambio, la creación de objetos gráficos y recursos y otros eventos importantes que afectan a varios fotogramas. Al mismo tiempo, puede capturar información detallada sobre fotogramas específicos, como llamadas de dibujo y envíos del sombreador de cálculo, así como los objetos Direct3D y los recursos subyacentes.  
  
### <a name="to-capture-a-frame"></a>Para capturar un fotograma  
  
-   En Visual Studio, en el **gráficos** barra de herramientas, haga clic en el **Capturar fotograma** botón ![icono de botón de captura de gráficos](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").  
  
-   En el teclado, presione la tecla Impr Pant.
  
    > [!NOTE]
    >  Mientras se ejecuta una aplicación en **diagnóstico de gráficos**, solo se puede utilizar la tecla Impr Pant para capturar un fotograma de información de gráficos; no realiza su función normal. Esto es así hasta que deja de capturar información de gráficos, generalmente deteniendo la depuración o saliendo normalmente de la aplicación, incluso si otra aplicación tiene el foco.  
  
-   En la interfaz de captura de Visual Studio, elija la **Capturar fotograma** situado debajo de la **sesión de diagnóstico** escala de tiempo, o elija el gran **Capturar fotograma** botón situada debajo de la **fotogramas por segundo** calle y a la derecha de los fotogramas capturados anteriormente. En la imagen siguiente, están resaltados los dos botones.  
  
     ![Capturar marcos con la herramienta de uso de la GPU.](media/pix_gpu_usage_tool_capture_frame.png)  
  
     Cuando esté listo para examinar los fotogramas capturados, inicie la **analizador de gráficos de Visual Studio** siguiendo el **marco...**  vínculo por encima de las imágenes en miniatura o haciendo doble clic en la miniatura.  
  
 Solo todo se pueden capturar fotogramas, por lo que cuando se inicia una captura, es realmente la información de gráficos desde el siguiente fotograma que se ha registrado. La grabación se inicia inmediatamente después de que aparece el fotograma en el que ha iniciado la captura y finaliza cuando aparece el fotograma capturado. Puede capturar tantos fotogramas como desee mientras la aplicación se ejecuta en Diagnóstico de gráficos. Si no captura ningún fotograma, se descarta el registro de gráficos.  
  
 Al capturar fotogramas, Visual Studio muestra la ventana de sesión de diagnóstico (.diagsession). Si cierra esta ventana, detenga la depuración o cerrar la aplicación, no se puede capturar más fotogramas en el registro. Para capturar más información de gráficos, tendrá que ejecutar de nuevo la aplicación en Diagnóstico de gráficos para que se inicie una nueva sesión de diagnóstico.  
  
### <a name="graphics-diagnostics-capture-options"></a>Opciones de captura de diagnóstico de gráficos  
 Puede configurar la captura de modo que recopile pilas de llamadas de todos los eventos de gráficos o un subconjunto limitado, deshabilitar la HUD de captura y habilitar o deshabilitar el modo de compatibilidad de captura.  
  
#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Para configurar las opciones de captura de diagnóstico de gráficos  
  
1.  En la barra de menús, elija Herramientas y Opciones. Aparecerá el cuadro de diálogo Opciones.  
  
2.  En la lista de categorías de las opciones de la izquierda, elija Diagnóstico de gráficos y, a continuación, configure las opciones de diagnóstico de gráficos que quiera.  
  
     **Recopilar pilas de llamadas durante la captura (ralentiza la captura)**  
     Active esta casilla para recopilar pilas de llamadas. Las pilas de llamadas no se recopilan de forma predeterminada. Para capturar las pilas de llamadas, asegúrese de que el **recopilar pilas de llamadas durante la captura (ralentiza la captura** casilla de verificación se establece para habilitar la recopilación y, a continuación, establecer el **para los marcadores draw, dispatch, present y perf**opción (valor predeterminado) para recopilar únicamente las pilas de llamadas más importantes, o la **para todo** opción para recopilar todas las pilas de llamada. Para detener la recopilación de pilas de llamadas más adelante, desactive la **recopilar pilas de llamadas durante la captura (ralentiza la captura** casilla de verificación.  
  
     **Deshabilitar HUD de juego durante la captura**  
     Active esta casilla para deshabilitar la superposición de HUD que suelen mostrar las aplicaciones que se ejecutan bajo el diagnóstico de gráficos. Desactívela para mostrar la superposición de HUD.  
  
     **Capturar en modo de compatibilidad**  
     Active esta casilla para capturar la información de gráficos en el modo de compatibilidad. La configuración predeterminada es la captura en modo de compatibilidad. En el modo de compatibilidad, Direct3D no informa de que la GPU admite más funciones que las definidas en el nivel de características de base. Así, se evita que la aplicación que se está capturando utilice extensiones específicas del hardware de la GPU donde se captura, y se garantiza que el registro de gráficos se pueda reproducir con cualquier GPU que admita un nivel de características igual o mayor. Desactive esta casilla para deshabilitar el modo de compatibilidad. Los registros capturados con el modo de compatibilidad deshabilitado no se reproducirán correctamente en las GPU que no admitan las mismas características adicionales que usó la aplicación durante la captura.  
  
     **Detener captura si se encuentra algún error de las capas SDK**  
     Active esta casilla para detener la captura inmediatamente si se producen errores.  
  
## <a name="capturing-graphics-information-remotely"></a>Capturar información de gráficos de forma remota  
 Se puede capturar información de gráficos desde una aplicación que se ejecute en el equipo local o en un dispositivo remoto. La captura remota se admite para los equipos [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] y dispositivos [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)]. Para capturar información de gráficos desde una aplicación que se ejecute de forma remota, configure el proyecto para la depuración remota y después ejecute la aplicación en Diagnóstico de gráficos tal como se ha descrito anteriormente. La aplicación se ejecuta en el equipo remoto y la información de gráficos capturada se registra en el equipo de desarrollo.  
  
 El modo en que configure el proyecto para la depuración remota dependerá del tipo de aplicación que esté desarrollando y del lenguaje de programación que utilice. Para obtener información acerca de cómo configurar la depuración remota para una aplicación de UWP, vea [UWP ejecutar aplicaciones en un equipo remoto](../run-windows-store-apps-on-a-remote-machine.md). Para obtener información acerca de cómo configurar la depuración remota para una aplicación de escritorio de Windows, vea [depuración remota](../remote-debugging.md).  
  
 Posteriormente, podrá utilizar un equipo o un dispositivo remoto para reproducir la información de los gráficos, independientemente del lugar donde se haya capturado la información. Para obtener más información, consulte [Cómo: cambiar la máquina de reproducción de diagnóstico de gráficos](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="capturing-graphics-information-from-the-command-line"></a>Captura de información de gráficos desde la línea de comandos  
 Se puede capturar información de los gráficos desde una aplicación con una herramienta de línea de comandos. Esta herramienta, DXCap.exe, puede capturar y reproducir rápidamente información de gráficos sin usar Visual Studio ni capturas de programación. En particular, puede utilizar DXCap.exe para la automatización o en un entorno de prueba. Para obtener más información sobre DXCap.exe, vea [herramienta de captura de línea de comandos](command-line-capture-tool.md)  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Capturar información de gráficos](walkthrough-capturing-graphics-information.md)