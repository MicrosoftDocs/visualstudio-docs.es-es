---
title: Captura de información de gráficos | Microsoft Docs
description: Capture información de gráficos desde la aplicación basada en Direct3D para que pueda usar el Analizador de gráficos de Visual Studio con el fin de diagnosticar problemas de representación y de rendimiento.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a11a5dc3a02959ff7bec4cfaac9aac2ca231b2ba
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727929"
---
# <a name="capturing-graphics-information"></a>Capturar información de gráficos
Capture información de gráficos desde la aplicación basada en Direct3D para que pueda usar el Analizador de gráficos de Visual Studio con el fin de diagnosticar problemas de representación y de rendimiento.

## <a name="capturing-graphics-information"></a>Capturar información de gráficos
 La captura de información de gráficos es un proceso de dos pasos. En primer lugar, ejecute la aplicación en Diagnóstico de gráficos y después especifique uno o varios fotogramas de los que desea capturar información detallada.

### <a name="to-run-your-app-under-graphics-diagnostics"></a>Para ejecutar la aplicación en Diagnóstico de gráficos

- En la barra de menús, elija **Depurar**, **Gráficos** e **Iniciar depuración de gráficos**. (Teclado: presione Alt+F5)

- En la barra de herramientas **Gráficos**, elija el botón **Iniciar depuración de gráficos**.

  Mientras se ejecuta una aplicación en Diagnóstico de gráficos, parte de la información de los gráficos se captura en todo momento; entre esta información se incluye la configuración del dispositivo, la creación de la cadena de intercambio, la creación de objetos gráficos y recursos y otros eventos importantes que afectan a varios fotogramas. Al mismo tiempo, puede capturar información detallada sobre fotogramas específicos, como llamadas de dibujo y envíos del sombreador de cálculo, así como los objetos Direct3D y los recursos subyacentes.

### <a name="to-capture-a-frame"></a>Para capturar un fotograma

- En Visual Studio, en la barra de herramientas **Gráficos**, haga clic en el botón **Capturar fotograma** ![Icono del botón de captura de gráficos](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").

- En el teclado, presione la tecla Imprimir pantalla.

  > [!NOTE]
  > Mientras se ejecuta una aplicación en **Diagnóstico de gráficos**, la tecla Imprimir pantalla solo se puede utilizar para capturar un fotograma de información de gráficos, es decir, no funciona como lo hace normalmente. Esto es así hasta que deja de capturar información de gráficos, generalmente deteniendo la depuración o saliendo normalmente de la aplicación, incluso si otra aplicación tiene el foco.

- En la interfaz de captura de Visual Studio, elija el botón **Capturar fotograma** situado debajo de la escala de tiempo **Sesión de diagnóstico** o elija el botón grande **Capturar fotograma** situado debajo de la calle **Fotogramas por segundo** y a la derecha de los fotogramas capturados anteriormente. En la imagen siguiente, están resaltados los dos botones.

   ![Capturar marcos con la herramienta de uso de la GPU.](media/pix_gpu_usage_tool_capture_frame.png)

   Cuando esté listo para examinar los fotogramas capturados, inicie el **Analizador de gráficos de Visual Studio** siguiendo el vínculo **Fotograma...** situado sobre las imágenes en miniatura o haciendo doble clic en la miniatura.

  Solo se pueden capturar fotogramas enteros, por lo que cuando inicia una captura, en realidad se registra la información de gráficos del siguiente fotograma. La grabación se inicia inmediatamente después de que aparece el fotograma en el que ha iniciado la captura y finaliza cuando aparece el fotograma capturado. Puede capturar tantos fotogramas como desee mientras la aplicación se ejecuta en Diagnóstico de gráficos. Si no captura ningún fotograma, se descarta el registro de gráficos.

  Al capturar fotogramas, Visual Studio muestra la ventana de sesión de diagnóstico (.diagsession). Si cierra esta ventana, detiene la depuración o cierra la aplicación, no podrá capturar más fotogramas en ese registro. Para capturar más información de gráficos, tendrá que ejecutar de nuevo la aplicación en Diagnóstico de gráficos para que se inicie una nueva sesión de diagnóstico.

### <a name="graphics-diagnostics-capture-options"></a>Opciones de captura de diagnóstico de gráficos
 Puede configurar la captura de modo que recopile pilas de llamadas de todos los eventos de gráficos o un subconjunto limitado, deshabilitar la HUD de captura y habilitar o deshabilitar el modo de compatibilidad de captura.

#### <a name="to-configure-graphics-diagnostics-capture-options"></a>Para configurar las opciones de captura de diagnóstico de gráficos

1. En la barra de menús, elija Herramientas y Opciones. Aparecerá el cuadro de diálogo Opciones.

2. En la lista de categorías de las opciones de la izquierda, elija Diagnóstico de gráficos y, a continuación, configure las opciones de diagnóstico de gráficos que quiera.

     **Recopilar pilas de llamadas durante la captura (ralentiza la captura)** : active esta casilla para recopilar pilas de llamadas. Las pilas de llamadas no se recopilan de forma predeterminada. Para capturar las pilas de llamadas, asegúrese de que esté activada la casilla **Recopilar pilas de llamadas durante la captura (ralentiza la captura)** para habilitar la recopilación y, después, establezca la opción **para los marcadores draw, dispatch, present y perf** (valor predeterminado) para recopilar únicamente las pilas de llamadas más importantes, o la opción **para todo** para recopilar todas las pilas de llamadas. Para detener la recopilación de pilas de llamadas más adelante, desactive la casilla **Recopilar pilas de llamadas durante la captura (ralentiza la captura)** .

     **Deshabilitar HUD de juego durante la captura**: active esta casilla para deshabilitar la superposición de HUD que suelen mostrar las aplicaciones que se ejecutan bajo el diagnóstico de gráficos. Desactívela para mostrar la superposición de HUD.

     **Captura en modo de compatibilidad**: active esta casilla para capturar la información de gráficos en el modo de compatibilidad. La configuración predeterminada es la captura en modo de compatibilidad. En el modo de compatibilidad, Direct3D no informa de que la GPU admite más funciones que las definidas en el nivel de características de base. Así, se evita que la aplicación que se está capturando utilice extensiones específicas del hardware de la GPU donde se captura, y se garantiza que el registro de gráficos se pueda reproducir con cualquier GPU que admita un nivel de características igual o mayor. Desactive esta casilla para deshabilitar el modo de compatibilidad. Los registros capturados con el modo de compatibilidad deshabilitado no se reproducirán correctamente en las GPU que no admitan las mismas características adicionales que usó la aplicación durante la captura.

     **Detención de la captura si se encuentran errores en las capas del SDK**: active esta casilla para detener la captura inmediatamente si se producen errores.

## <a name="capturing-graphics-information-remotely"></a>Capturar información de gráficos de forma remota
 Se puede capturar información de gráficos desde una aplicación que se ejecute en el equipo local o en un dispositivo remoto. La captura remota se admite para los equipos [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)] y dispositivos [!INCLUDE[winblue_winrt_2](../includes/winblue_winrt_2_md.md)]. Para capturar información de gráficos desde una aplicación que se ejecute de forma remota, configure el proyecto para la depuración remota y después ejecute la aplicación en Diagnóstico de gráficos tal como se ha descrito anteriormente. La aplicación se ejecuta en el equipo remoto y la información de gráficos capturada se registra en el equipo de desarrollo.

 El modo en que configure el proyecto para la depuración remota dependerá del tipo de aplicación que esté desarrollando y del lenguaje de programación que utilice. Para obtener información sobre cómo configurar la depuración remota de una aplicación para UWP, vea [Ejecutar aplicaciones para UWP en un equipo remoto](../run-windows-store-apps-on-a-remote-machine.md). Para obtener información sobre cómo configurar la depuración remota para una aplicación de escritorio de Windows, vea [Depuración remota](../remote-debugging.md).

 Posteriormente, podrá utilizar un equipo o un dispositivo remoto para reproducir la información de los gráficos, independientemente del lugar donde se haya capturado la información. Para obtener más información, vea [Cómo: Cambio de la máquina de reproducción de Diagnóstico de gráficos](how-to-change-the-graphics-diagnostics-playback-machine.md).

## <a name="capturing-graphics-information-from-the-command-line"></a>Captura de información de gráficos desde la línea de comandos
 Se puede capturar información de los gráficos desde una aplicación con una herramienta de línea de comandos. Esta herramienta, DXCap.exe, puede capturar y reproducir rápidamente información de gráficos sin usar Visual Studio ni capturas de programación. En particular, puede utilizar DXCap.exe para la automatización o en un entorno de prueba. Para obtener más información sobre DXCap.exe, vea [Herramienta de captura de línea de comandos](command-line-capture-tool.md).

## <a name="see-also"></a>Vea también
- [Tutorial: Captura de información de gráficos](walkthrough-capturing-graphics-information.md)