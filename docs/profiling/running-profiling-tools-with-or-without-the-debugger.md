---
title: Ejecución de herramientas de generación de perfiles con o sin el depurador | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed4cf1cce3ba677b5232c86b7abb1386d4d1dc50
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597538"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Ejecutar herramientas de generación de perfiles con o sin el depurador

Visual Studio ofrece varias herramientas de generación de perfiles y medición del rendimiento. Algunas herramientas, como **Uso de CPU** y **Uso de memoria**, pueden ejecutarse con o sin el depurador, y en las configuraciones de compilación de depuración o de publicación. Las herramientas de **Generador de perfiles de rendimiento** como **Escala de tiempo de la aplicación** pueden ejecutarse en compilaciones de depuración o versión. Las herramientas integradas del depurador, como la ventana **Herramientas de diagnóstico** y la pestaña **Eventos** solo se ejecutan durante las sesiones de depuración.

>[!NOTE]
>Puede usar las herramientas de rendimiento sin depurador con Windows 7 y versiones posteriores. Se necesita Windows 8 o versiones posteriores para ejecutar las herramientas de generación de perfiles integradas del depurador.

El **Generador de perfiles de rendimiento** sin depurador y las **Herramientas de diagnóstico** integradas en el depurador proporcionan información y experiencias diferentes. Las herramientas integradas del depurador muestran los puntos de interrupción y los valores de variable. Las herramientas sin depurador ofrecen resultados más cercanos a la experiencia del usuario final.

Para ayudarle a decidir qué herramientas y resultados debe utilizar, tenga en cuenta lo siguiente:

- Los problemas de rendimiento externo, como problemas de la capacidad de respuesta de la red o de E/S de archivos, no se diferenciarán demasiado en las herramientas con o sin depurador.
- Para problemas causados por llamadas con gran consumo de CPU, puede haber diferencias de rendimiento considerables entre las compilaciones de lanzamiento y de depuración. Compruebe si el problema existe en las compilaciones de versión.
- Si el problema se produce solo durante las compilaciones de depuración, probablemente no necesitará ejecutar las herramientas sin depurador. Para los problemas de compilaciones de versión, deberá decidir si las herramientas del depurador le ayudarán en la investigación.
- Las compilaciones de versión proporcionan optimizaciones como la inclusión de llamadas a funciones y constantes, la eliminación de rutas de acceso a código sin usar y el almacenamiento de variables de manera que no las pueda usar el depurador. Los números de rendimiento de las herramientas integradas del depurador son menos precisos, porque las compilaciones de depuración carecen de estas optimizaciones.
- El propio depurador cambia los tiempos de rendimiento ya que realiza operaciones de depurador necesarias como interceptar excepciones y modular eventos de carga.
- Los números de rendimiento de la compilación de versión en las herramientas de **Generador de perfiles de rendimiento** son más precisos y exactos. Los resultados de la herramienta integrada del depurador son más útiles si se comparan con otras medidas relacionadas con la depuración.

##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Recopilar datos de generación de perfiles durante la depuración

Al comenzar la depuración en Visual Studio seleccionando **Depurar** > **Iniciar depuración** o presionando **F5**, la ventana **Herramientas de diagnóstico** aparece de forma predeterminada. Para abrirla manualmente, seleccione **Depurar** > **Ventanas** > **Mostrar herramientas de diagnóstico**. En la ventana **Herramientas de diagnóstico** se muestra información sobre el uso de CPU, la memoria de proceso y los eventos.

![Herramientas de diagnóstico](../profiling/media/diagnostictools-update1.png "Diagnostic Tools")

- Use el icono **Configuración** en la barra de herramientas para seleccionar si quiere ver el **Uso de memoria**, el **Análisis de UI**, y el **Uso de CPU**.

- Seleccione **Configuración** en la lista desplegable **Configuración** para abrir las **páginas de propiedades de las Herramientas de diagnóstico** con más opciones.

- Si ejecuta Visual Studio Enterprise, puede habilitar o deshabilitar IntelliTrace en Visual Studio en **Herramientas** > **Opciones** > **IntelliTrace**.

La sesión de diagnóstico termina cuando se detiene la depuración.

También puede ver **Herramientas de diagnóstico** para destinos de depuración remotos. Para la depuración remota y la generación de perfiles, el depurador remoto de Visual Studio debe estar instalado y ejecutándose en el destino remoto.
- Para la depuración remota y la generación de perfiles de los proyectos de aplicaciones de escritorio, vea [Remote debugging](../debugger/remote-debugging.md) (Depuración remota).
- Para la depuración remota y la generación de perfiles de aplicaciones para UWP, vea [Depurar aplicaciones para UWP en equipos remotos desde Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

### <a name="the-events-tab"></a>La pestaña Eventos

Durante una sesión de depuración, en la pestaña **Eventos** de la ventana **Herramientas de diagnóstico** se enumeran los eventos de diagnóstico que se producen. Los prefijos de categoría: **Punto de interrupción**, **Archivo** y otros, permiten examinar rápidamente la lista en busca de una categoría u omitir las categorías que no interesan.

Use la lista desplegable **Filtro** para filtrar los eventos dentro y fuera de la vista seleccionando o anulando la selección de categorías de eventos concretas.

![Filtro de eventos de diagnóstico](../profiling/media/diagnosticeventfilter.png "Diagnostic Event Filter")

Use el cuadro de búsqueda para encontrar una cadena concreta en la lista de eventos. Estos son los resultados de una búsqueda de la cadena "name" que coincide con cuatro eventos:

![Búsqueda de eventos de diagnóstico](../profiling/media/diagnosticseventsearch.png "Diagnostic Event Search")

Para más información, consulte [Búsqueda y filtrado de la pestaña Eventos de la ventana de herramientas de diagnóstico](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Recopilar datos de generación de perfiles sin depurar

Para recopilar datos de rendimiento sin depuración, puede ejecutar las herramientas de **Generador de perfiles de rendimiento**. Algunas de las herramientas de generación de perfiles requieren privilegios de administrador para ejecutarse. Puede ejecutar Visual Studio como administrador o puede ejecutar las herramientas como administrador al iniciar la sesión de diagnóstico.

1. Con un proyecto abierto en Visual Studio, seleccione **Depurar** > **Generador de perfiles de rendimiento** o presione **Alt**+**F2**.

1. En la página de inicio de diagnóstico, elija una o varias herramientas para ejecutarlas. Solo se muestran las herramientas que se pueden aplicar para el tipo de proyecto, el sistema operativo y el lenguaje de programación. Haga clic en **Mostrar todas las herramientas** para ver también herramientas que están deshabilitadas para esta sesión de diagnóstico. Este es el aspecto que podrían tener las opciones para una aplicación UWP de C#:

   ![Seleccionar las herramientas de diagnóstico](../profiling/media/diag_selecttool.png "DIAG_SelectTool")

1. Para iniciar la sesión de diagnóstico, haga clic en **Iniciar**.

   Mientras se ejecuta la sesión, algunas herramientas muestran gráficos de datos en tiempo real en la página de las herramientas de diagnóstico.

    ![Recopilar datos en la página Centro de rendimiento y diagnósticos](../profiling/media/pdhub_collectdata.png "Recopilar datos del centro")

1. Para finalizar la sesión de diagnóstico, haga clic en **Detener recopilación**.

   Los datos analizados se muestran en la página **Informe**.

Puede guardar los informes y abrirlos desde la lista **Sesiones abiertas recientemente** en la página de inicio de las herramientas de diagnóstico.

![Abrir un archivo de sesión de diagnóstico guardada](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

### <a name="the-profiling-report"></a>El informe de generación de perfiles
 ![Informe de herramientas de diagnóstico](../profiling/media/diag_report.png "DIAG_Report")

|||
|-|-|
|![Paso 1](../profiling/media/procguid_1.png "ProcGuid_1")|La escala de tiempo muestra la longitud de la sesión de generación de perfiles, los eventos de activación del ciclo de vida de la aplicación y las marcas de usuario.|
|![Paso 2](../profiling/media/procguid_2.png "ProcGuid_2")|Puedes restringir el informe a una parte de la escala de tiempo arrastrando las barras azules para seleccionar una región de esta.|
|![Paso 3](../profiling/media/procguid_3.png "ProcGuid_3")|Cada herramienta muestra uno o varios gráficos maestros. Si la sesión de diagnóstico tenía más de una herramienta, se muestran todos los gráficos maestros.|
|![Paso 4](../profiling/media/procguid_4.png "ProcGuid_4")|Puede contraer y expandir los gráficos individuales de cada herramienta.|
|![Paso 5](../profiling/media/procguid_6.png "ProcGuid_6")|Cuando los datos incluyen más de una herramienta, los detalles de la herramienta se recopilan bajo pestañas.|
|![Paso 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|En la mitad inferior del informe se muestra una o varias vistas detalladas para cada herramienta. Puede filtrar la vista seleccionado regiones de la escala de tiempo.|

## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>Ejecutar sesiones de diagnóstico en aplicaciones instaladas o en ejecución

 Además de iniciar la aplicación desde el proyecto de Visual Studio, también puede ejecutar sesiones de diagnóstico en destinos alternativos. Por ejemplo, puede que le interese diagnosticar problemas de rendimiento en una aplicación que se instaló desde la Tienda de aplicaciones Windows.

 ![Elegir destino de análisis de herramientas de diagnóstico](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")

 Puede iniciar las aplicaciones que ya están instaladas o puede asociar las herramientas de diagnóstico a aplicaciones y procesos que se están ejecutando. Cuando seleccione **Aplicación en ejecución** o **Aplicación instalada**, selecciona la aplicación de una lista que busca las aplicaciones en el destino de implementación especificado. Este destino puede ser un equipo local o remoto.

 ![Elegir una aplicación instalada o en ejecución para el diagnóstico](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")

## <a name="see-also"></a>Vea también

A continuación hay entradas de blog y artículos de MSDN del equipo de desarrollo de diagnóstico:
- [MSDN Magazine: Analyze Performance While Debugging in Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx) (Analizar el rendimiento durante la depuración en Visual Studio 2015)

- [MSDN Magazine: Use IntelliTrace to Diagnose Issues Faster](https://msdn.microsoft.com/magazine/dn973014.aspx) (Usar IntelliTrace para diagnosticar problemas con mayor rapidez)

- [Entrada de blog: Diagnosing Event Handler Leaks with the Memory Usage Tool in Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/) (Diagnosticar fugas del controlador de eventos con la herramienta de uso de memoria en Visual Studio 2015)

- [Vídeo: Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716) (Depuración histórica con IntelliTrace en Microsoft Visual Studio Ultimate 2015)

- [Vídeo: Debugging Performance Issues Using Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731) (Depurar problemas de rendimiento con Visual Studio 2015)

- [Sugerencias de rendimiento: Performance Information at-a-glance while Debugging with Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/) (Información de rendimiento de un solo vistazo mientras se realiza la depuración con Visual Studio)

- [Ventana del depurador de Herramientas de diagnóstico en Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)

- [IntelliTrace en Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
