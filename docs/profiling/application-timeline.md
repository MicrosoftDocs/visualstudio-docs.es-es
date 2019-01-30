---
title: Análisis del consumo de recursos en aplicaciones XAML
ms.custom: seodec18
ms.date: 11/01/2018
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: ebba86ae6683ecce39a1246ac92fc714d6649a89
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948614"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Análisis del consumo de recursos y la actividad del subproceso de interfaz de usuario (XAML)

Use la **escala de tiempo de aplicación** del generador de perfiles para buscar y corregir en aplicaciones XAML los problemas de rendimiento relacionados con la interacción. Esta herramienta ayuda a mejorar el rendimiento de la aplicación XAML al mostrar una vista detallada del consumo de recursos de las aplicaciones. Puede analizar el tiempo consumido por la aplicación en la preparación de marcos de la interfaz de usuario (diseño y presentación), la atención de solicitudes de red y de disco y escenarios tales como el inicio de la aplicación, la carga de la página y el cambio de tamaño de las ventanas.

**Escala de tiempo de aplicación** es una de las herramientas que puede iniciar con el comando **Depurar** > **Generador de perfiles de rendimiento**.

Esta herramienta reemplaza a **Capacidad de respuesta de la IU de XAML** , que formaba parte del conjunto de herramientas de diagnóstico de Visual Studio 2013.

Puede utilizar esta herramienta en las siguientes plataformas:

- Aplicaciones Windows universales (en Windows 10)
- Windows 8.1
- Windows Presentation Foundation (.NET 4.0 y posterior)
- Windows 7

> [!NOTE]
> Puede recopilar y analizar datos de uso de CPU y de consumo de energía junto con los datos de la **Escala de tiempo de aplicación** . Vea [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).
  
## <a name="collect-application-timeline-data"></a>Recopilar datos de la escala de tiempo de aplicación

Puede generar perfiles de capacidad de respuesta de la aplicación en su máquina local, en un dispositivo conectado, en un simulador o emulador de Visual Studio o un dispositivo remoto. Vea [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

> [!TIP]
> Si es posible, ejecute la aplicación directamente en el dispositivo. El rendimiento de la aplicación observado en el simulador o a través de una conexión a escritorio remoto puede no ser igual al rendimiento real en el dispositivo. Por otro lado, la recopilación de datos mediante Herramientas remotas de Visual Studio no afecta a los datos de rendimiento.  

Estos son los pasos básicos:  

1. Abra la aplicación XAML.

2. Haga clic en **Depurar / Generador de perfiles de rendimiento**. Debería ver una lista de herramientas de generación de perfiles en la ventana .diagsession.

3. Seleccione **Escala de tiempo de aplicación** y luego haga clic en **Iniciar** en la parte inferior de la ventana.

   > [!NOTE]
   > Es posible que vea una ventana Control de cuentas de usuario en la que se le solicita permiso para ejecutar *VsEtwCollector.exe*. Haga clic en **Sí**.

4. Ejecute el escenario del que quiera generar un perfil en su aplicación para recopilar datos de rendimiento.

5. Para detener la generación de perfiles, vuelva a la ventana .diagsession y haga clic en **Detener** en la parte superior.

   Visual Studio analiza los datos recopilados y muestra los resultados.

   ![Informe del generador de perfiles de la escala de tiempo](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Analizar datos de generación de perfiles de escala de tiempo

Después de obtener los datos de la generación de perfiles, puede seguir estos pasos para iniciar el análisis:  
  
1. Vea la información de los gráficos **Uso del subproceso de UI** y **Rendimiento visual (FPS)** y, luego, use las barras de navegación de la escala de tiempo para seleccionar un intervalo de tiempo que quiera analizar.  
  
2. Con la información de los gráficos **Uso del subproceso de UI** o **Rendimiento visual (FPS)**, examine los detalles de la vista **Detalles de la escala de tiempo** para detectar las posibles causas de cualquier falta de capacidad de respuesta aparente.
  
### <a name="BKMK_Report_scenarios_categories_and_events"></a> Informes de escenarios, categorías y eventos  

La herramienta **Escala de tiempo de aplicación** muestra datos de tiempo para escenarios, categorías y eventos relacionados con el rendimiento de XAML.  

### <a name="BKMK_Diagnostic_session_timeline"></a> Escala de tiempo de la sesión de diagnóstico  

![Escala de tiempo de rendimiento y diagnósticos](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")  

La regla que aparece en la parte superior de la página muestra la escala de tiempo para la información cuyo perfil se ha generado. Esta escala de tiempo se aplica a los gráficos **Utilización del subproceso de IU** y **Rendimiento visual** . Puedes restringir el ámbito del informe arrastrando las barras de navegación en la escala de tiempo para seleccionar un segmento de esta.  

La escala de tiempo también muestra cualquier marca de usuario que haya insertado, así como los eventos del ciclo de vida de activación de la aplicación.  

### <a name="BKMK_UI_thread_utilization_graph"></a> Gráfico de utilización del subproceso de IU

![Gráfico de utilización de CPU](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")  

El gráfico **Utilización del subproceso de UI (%)** es un gráfico de barras que muestra la cantidad relativa de tiempo empleado en una categoría durante un intervalo de la colección.  

### <a name="BKMK_Visual_throughput_FPS_graph"></a> Gráfico de rendimiento visual (FPS)  

![Gráfico de rendimiento visual](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")  

El gráfico de líneas **Rendimiento visual (FPS)** muestra los fotogramas por segundo (FPS) en el subproceso de interfaz de usuario y de composición de la aplicación.  

### <a name="BKMK_Timeline_details_"></a> Detalles de la escala de tiempo  

En la vista de detalles es donde se invierte la mayor parte del tiempo en el análisis del informe. Muestra el uso de CPU de la aplicación en dos categorías: el subsistema Marco de trabajo de la interfaz de usuario o el componente del sistema que ha consumido la CPU.

Se admiten los siguientes eventos:  

|||  
|-|-|  
|**Análisis**|Tiempo invertido en analizar archivos XAML y crear objetos.<br /><br /> Si se expande un nodo **Análisis** de **Detalles de la escala de tiempo**, se muestra la cadena de dependencia de todos los archivos XAML que se han analizado como resultado del evento raíz. Esta sugerencia permite identificar análisis de archivos y creación de objetos innecesarios en escenarios sensibles al rendimiento y optimizarlos.|  
|**Diseño**|En aplicaciones grandes, pueden mostrarse miles de elementos en la pantalla al mismo tiempo. Esta pantalla podría dar lugar a una baja velocidad de fotogramas de la UI y, por tanto, una mala capacidad de respuesta de la aplicación. El evento de diseño determina con precisión el costo de implementar cada elemento (es decir, el tiempo invertido en Arrange, Measure, ApplyTemplate, ArrangeOverride y MeasureOverride). También compila los árboles visuales que han participado en un cálculo de diseño. Puede usar esta visualización para determinar qué árboles lógicos debe eliminar o para evaluar otros mecanismos de aplazamiento a fin de optimizar el cálculo de diseño.|  
|**Representar**|Tiempo invertido en representar elementos XAML en la pantalla.|  
|**E/S**|Tiempo invertido en recuperar datos desde el disco local o desde recursos de red a los que se tiene acceso mediante la API [Microsoft Windows Internet (WinINet)](/windows/desktop/WinInet/portal).|  
|**Código de aplicación**|Tiempo invertido en la ejecución de código (de usuario) de la aplicación no relacionado con el análisis ni el diseño.|  
|**Otro XAML**|Tiempo invertido en ejecutar código en tiempo de ejecución XAML.|  
  
> [!TIP]
> Elija la herramienta **Uso de CPU** junto con la herramienta **Escala de tiempo de aplicación** al comenzar a generar perfiles para ver los métodos de aplicación que se ejecutan en el subproceso de UI. Mover el código de la aplicación de larga duración a un subproceso en segundo plano puede mejorar la capacidad de respuesta de la UI.  
  
#### <a name="BKMK_Customizing_Timeline_details_"></a> Personalizar detalles de escala de tiempo  

Utilice la barra de herramientas **Detalles de la escala de tiempo** para ordenar, filtrar y especificar las anotaciones de las entradas de la vista **Detalles de la escala de tiempo** .  
  
|||  
|-|-|  
|**Ordenar por**|Ordenar por hora de inicio o longitud de los eventos.|  
|![Agrupar eventos por fotograma](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Agrega o quita una categoría **Marco** de nivel superior que agrupa eventos por marco.|  
|![Filtrar la lista de detalles de la escala de tiempo](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Filtra la lista por categorías seleccionadas y la longitud de los eventos.|  
|![Personalizar la información de detalles de la escala de tiempo](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Permite especificar las anotaciones de eventos.|  
  
## <a name="see-also"></a>Vea también

- [WPF team blog: New UI Performance analysis tool for WPF applications](https://blogs.msdn.microsoft.com/wpf/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications/) (Blog del equipo de WPF: Nueva herramienta de análisis de rendimiento de interfaz de usuario para aplicaciones para WPF)  
- [Procedimientos recomendados de rendimiento para aplicaciones para UWP con C++, C# y Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Optimizar el rendimiento de las aplicaciones WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)  
- [Generación de perfiles en Visual Studio](../profiling/index.md)  
- [Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md)
