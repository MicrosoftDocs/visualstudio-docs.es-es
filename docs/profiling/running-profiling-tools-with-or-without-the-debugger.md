---
title: Ejecutar herramientas de generación de perfiles con o sin el depurador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e5197ba9e1a2fda9cb6a41cfe903bd772db53331
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2018
ms.locfileid: "42627012"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Ejecutar herramientas de generación de perfiles con o sin el depurador
Visual Studio ahora ofrece herramientas de rendimiento, algunas de las cuales (por ejemplo, **Uso de la CPU** y **Uso de la memoria**) se pueden ejecutar con o sin el depurador. Las herramientas de rendimiento sin depurador están diseñadas para ejecutarse en las configuraciones de la versión, mientras que las herramientas integradas en el depurador están diseñadas para ejecutarse en las configuraciones de depuración.  

Las herramientas de generación de perfiles se pueden usar sin el depurador en Windows 7 y versiones posteriores. Para ejecutar las herramientas de generación de perfiles con el depurador se requiere Windows 8 y versiones posteriores (ventana **Herramientas de diagnóstico**).
  
## <a name="should-i-run-the-tool-with-or-without-the-debugger"></a>¿Debería ejecutar la herramienta con o sin el depurador?  
 Las herramientas de rendimiento integradas en el depurador permiten hacer muchas cosas que las herramientas sin depurador no pueden hacer, como establecer puntos de interrupción y examinar los valores de las variables. Las herramientas sin depurador ofrecen una experiencia más próxima a la que verán los usuarios de la aplicación comercial.  
  
 Estas son algunas preguntas que pueden ayudarle a decidir qué tipo de herramienta es apropiada para sus fines:  
  
1.  ¿Se detectó el problema mientras la aplicación se estaba desarrollando o fue en una versión lanzamiento?  
  
     Si detectó el problema en la fase de desarrollo, probablemente no necesitará ejecutar las herramientas de rendimiento en una versión de lanzamiento. Si lo detectó en una versión de lanzamiento, debe reproducir el problema con una configuración de versión y, a continuación, decidir si el depurador le ayudaría a realizar una investigación más detallada.  
  
2.  ¿Se debe el problema a un proceso intensivo de la CPU?  
  
     Muchos problemas se deben a problemas de rendimiento externo, como E/S de archivos o la capacidad de respuesta de la red, por lo que hay mucha diferencia si se ejecutan las herramientas de rendimiento con o sin el depurador. Si el problema se debe a un gran número de llamadas a la CPU, la diferencia entre las configuraciones de lanzamiento y de depuración puede ser considerable y, probablemente, debe comprobar si el problema existe en la versión de compilación antes de utilizar las herramientas integradas en el depurador  
  
3.  ¿Es necesario medir con precisión el rendimiento o se acepta un número aproximado?  
  
     Las compilaciones de depuración carecen de ciertas optimizaciones que proporcionan las versiones de lanzamiento, por ejemplo la inclusión de llamadas a funciones y constantes, la eliminación de rutas de acceso a código sin usar y el almacenaje de las variables de manera que no las pueda usar el depurador. El propio depurador cambia los tiempos de rendimiento porque realiza ciertas operaciones que son necesarios para la depuración (por ejemplo, interceptar excepciones y eventos del módulo de carga). Los números de rendimiento de las herramientas integradas del depurador son menos precisos ya que no se tienen en cuenta para las optimizaciones del depurador, pero pueden seguir siendo útiles cuando se comparan con otras medidas relativas tomadas durante la depuración. Los números de rendimiento para las configuraciones de lanzamiento con las herramientas sin depurador son mucho más precisos.
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Recopilar datos de generación de perfiles durante la depuración  
 La siguiente sección trata la depuración local. En secciones posteriores puede encontrar información sobre la depuración en un dispositivo y la depuración remota.  
  
1.  Abra el proyecto que quiere depurar y luego haga clic en **Depurar** > **Iniciar depuración** (o en **Iniciar** en la barra de herramientas o presione **F5**).  
  
2.  La ventana **Herramientas de diagnóstico** aparece automáticamente a no ser que la desactive. Para que la ventana se vuelva a mostrar, haga clic en **Depurar** > **Windows** > **Mostrar Herramientas de diagnóstico**.  
  
3.  Ejecute los escenarios cuyos datos desea recopilar.  
  
     Mientras se ejecuta la sesión, puede ver información sobre eventos, memoria de procesos y uso de CPU.  
  
     En el gráfico siguiente se muestra la ventana de **Herramientas de diagnóstico** en Visual Studio 2015 Update 1:  
  
     ![DiagnosticTools Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
4.  Puede elegir si ve el **Uso de memoria** o el **Uso de CPU** (o ambos) con el ajuste **Seleccionar herramientas** en la barra de herramientas. Si ejecuta Visual Studio Enterprise, puede habilitar o deshabilitar IntelliTrace en **Herramientas** > **Opciones** > **IntelliTrace**.  
  
5.  La sesión de diagnóstico termina cuando se detiene la depuración.  
  
 En Visual Studio 2015 Update 1, la ventana **Herramientas de diagnóstico** le facilita centrarse en los eventos que le interesan.   Ahora se muestran los nombres de evento con prefijos de categoría (**Gesto**, **Salida del programa**, **Punto de interrupción**, **Archivo**, etc.) por lo que puede examinar la lista para buscar una categoría determinada u omitir las categorías que no le interesan rápidamente.  
  
 La ventana ahora tiene un cuadro de búsqueda para que pueda encontrar una cadena específica en cualquier lugar de la lista de eventos. Por ejemplo, el siguiente gráfico muestra los resultados de una búsqueda de la cadena "install", con la que coinciden cuatro eventos:  
  
 ![DiagnosticsEventSearch](../profiling/media/diagnosticseventsearch.png "DiagnosticsEventSearch")  
  
 También puede filtrar eventos para que se muestren o no en la vista en la ventana. En la lista desplegable **Filtrar** , puede activar o desactivar categorías de eventos concretas: Los nombres de categoría son los mismos que los nombres de prefijo.  
  
 ![DiagnosticEventFilter](../profiling/media/diagnosticeventfilter.png "DiagnosticEventFilter")  
  
 Para más información, consulte [Búsqueda y filtrado de la pestaña Eventos de la ventana de herramientas de diagnóstico](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window.aspx).  
  
## <a name="collect-profiling-data-without-debugging"></a>Recopilar datos de generación de perfiles sin depurar  
 Algunas herramientas de generación de perfiles requieren privilegios de administrador para ejecutarse. Puede ejecutar Visual Studio como administrador o puede optar por ejecutar las herramientas como administrador al iniciar la sesión de diagnóstico.  
  
1.  Abra el proyecto en Visual Studio.  
  
2.  En el menú **Depurar**, elija **Generador de perfiles de rendimiento** (tecla de método abreviado: **Alt**+**F2**).  
  
3.  En la página de inicio de diagnóstico, elija una o varias herramientas para ejecutarlas en la sesión. Solo se muestran las herramientas que se pueden aplicar para el tipo de proyecto, el sistema operativo y el lenguaje de programación. Al elegir una herramienta de diagnóstico, se deshabilitan las selecciones de las herramientas que no se pueden ejecutar en la misma sesión de diagnóstico. Este es el aspecto que podrían tener las opciones para una aplicación UWP de C#:  
  
     ![Seleccionar las herramientas de diagnóstico](../profiling/media/diag_selecttool.png "DIAG_SelectTool")  
  
4.  Para iniciar la sesión de diagnóstico, haga clic en **Iniciar**.  
  
5.  Ejecute los escenarios para los que desea recopilar datos.  
  
     Mientras se ejecuta la sesión, algunas herramientas muestran gráficos de datos en tiempo real en la página de inicio de las herramientas de diagnóstico.  
  
     ![Recopilar datos en la página Rendimiento y diagnósticos](../profiling/media/pdhub_collectdata.png "PDHUB_CollectData")  
  
6.  Para finalizar la sesión de diagnóstico, haga clic en **Detener recopilación**.  
  
 Cuando detiene la recopilación de datos de una sesión de diagnóstico, se analizan los datos y se muestra el informe en la página Diagnóstico.  
  
 También puede abrir archivos de sesión .diagnostic guardados de la lista abierta recientemente en la página de inicio de las herramientas de diagnóstico.  
  
 ![Abrir un archivo de sesión de diagnóstico guardada](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
## <a name="the-profiling-report"></a>El informe de generación de perfiles  
 ![Informe de herramientas de diagnóstico](../profiling/media/diag_report.png "DIAG_Report")  
  
|||  
|-|-|  
|![Paso 1](../profiling/media/procguid_1.png "ProcGuid_1")|La escala de tiempo muestra la longitud de la sesión de generación de perfiles, los eventos de activación del ciclo de vida de la aplicación y las marcas de usuario.|  
|![Paso 2](../profiling/media/procguid_2.png "ProcGuid_2")|Puedes restringir el informe a una parte de la escala de tiempo arrastrando las barras azules para seleccionar una región de esta.|  
|![Paso 3](../profiling/media/procguid_3.png "ProcGuid_3")|Una herramienta muestra uno o varios gráficos maestros. Si la sesión de diagnóstico se crea con varias herramientas, se muestran todos los gráficos maestros.|  
|![Paso 4](../profiling/media/procguid_4.png "ProcGuid_4")|Puede contraer y expandir los gráficos individuales.|  
|![Paso 5](../profiling/media/procguid_6.png "ProcGuid_6")|Si los datos incluyen información de varias herramientas, los detalles de la herramienta se recopilan bajo pestañas.|  
|![Paso 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|Una herramienta puede tener una o varias vistas de detalle. La vista se filtra por la región seleccionada de la escala de tiempo.|  
  
## <a name="set-the-analysis-target-to-another-device"></a>Establecer el destino del análisis a otro dispositivo  
 Además de iniciar la aplicación desde el proyecto de Visual Studio, también puede ejecutar sesiones de diagnóstico en destinos alternativos. Por ejemplo, puede que le interese diagnosticar problemas de rendimiento en una versión de la aplicación que se instaló desde la Tienda de aplicaciones Windows.  
  
 ![Elegir destino de análisis de herramientas de diagnóstico](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 Puede iniciar las aplicaciones que ya están instaladas en un dispositivo o puede asociar las herramientas de diagnóstico a algunas aplicaciones que se están ejecutando. Cuando elige **Aplicación en ejecución** o **Aplicación instalada**, selecciona la aplicación de una lista que muestra las aplicaciones en el destino de implementación especificado.  
  
 ![Elegir una aplicación instalada o en ejecución para el diagnóstico](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")  
  
 Al elegir **Internet Explorer**, puede especificar la dirección URL y cambiar el destino de implementación del teléfono.  
  
 ![Especificar la dirección URL que se mostrará en Internet Explorer](../profiling/media/pdhub_choosephoneanalysistarget.png "PDHUB_ChoosePhoneAnalysisTarget")  
  
## <a name="remote-debugging"></a>Remote Debugging  
 Ejecutar una sesión de diagnóstico en un equipo remoto o una tableta requiere instalar en el destino remoto las herramientas remotas de Visual Studio. Para aplicaciones de escritorio, consulte [Depuración remota](../debugger/remote-debugging.md).  En el caso de las aplicaciones UWP, vea [Ejecutar aplicaciones para UWP en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
## <a name="blog-posts-and-msdn-articles-from-the-diagnostics-development-team"></a>Entradas de blog y artículos de MSDN del equipo de desarrollo de diagnóstico  
 [MSDN Magazine: Analizar el rendimiento durante la depuración en Visual Studio 2015](https://msdn.microsoft.com/en-us/magazine/dn973013.aspx)  
  
 [MSDN Magazine: Usar IntelliTrace para diagnosticar problemas](https://msdn.microsoft.com/en-us/magazine/dn973014.aspx)  
  
 [Entrada de blog: Diagnosticar pérdidas del controlador de eventos con la herramienta de uso de memoria en Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/04/29/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015.aspx)  
  
 [Vídeo: Depuración histórica con IntelliTrace en Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)  
  
 [Vídeo: Depurar problemas de rendimiento con Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)  
  
 [PerfTips: Información de rendimiento de un vistazo mientras se depura con Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx)  
  
 [Ventana del depurador de Herramientas de diagnóstico en Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015.aspx)  
  
 [IntelliTrace en Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)
