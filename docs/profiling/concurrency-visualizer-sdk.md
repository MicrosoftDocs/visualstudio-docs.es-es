---
title: "SDK del Visualizador de simultaneidad | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.sdk.about"
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SDK del Visualizador de simultaneidad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se puede instrumentar el código fuente mediante el SDK del Visualizador de simultaneidad para mostrar información adicional en el Visualizador de simultaneidad.  Se pueden asociar los datos adicionales con fases y eventos del código.  Estas visualizaciones adicionales se conocen como *marcadores*.  Para un tutorial de introducción, [Introducción del visualizador de simultaneidad SDK](http://go.microsoft.com/fwlink/?LinkId=235405)vea.  
  
## Propiedades  
 Las marcas, los intervalos y los mensajes tienen dos propiedades: categoría e importancia.  En el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), se pueden usar estas propiedades para filtrar el conjunto de marcadores que aparecen.  Además, estas propiedades afectan a la representación visual de los marcadores.  Por ejemplo, el tamaño de las marcas se usa para representar la importancia.  Asimismo, el color se usa para indicar la categoría.  
  
## Uso básico  
 El Visualizador de simultaneidad expone un proveedor predeterminado que se puede utilizar para generar marcadores.  El proveedor ya está registrado junto con el Visualizador de simultaneidad y no se tiene que hacer nada más para conseguir que los marcadores aparezcan en la interfaz de usuario.  
  
### Visual Basic y C\#  
 En C\#, Visual basic y otro código administrado, use el proveedor predeterminado llamando a <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>.  Expone cuatro funciones para generar marcadores: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A> y <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>.  Hay múltiples sobrecargas para estas funciones, según se quieran usar los predeterminados para estas propiedades.  La sobrecarga más simple toma sólo un parámetro de cadena que especifica la descripción del evento.  Se muestra la descripción en los informes del Visualizador de simultaneidad.  
  
##### Para agregar soporte SDK al proyecto de C\# o de Visual Basic  
  
1.  En la barra de menús, elija **Analizar**, **Visualizador de Simultaneidad**, **Agregar SDK al proyecto**.  
  
2.  Seleccione el proyecto en el que se quiere obtener acceso al SDK y luego elija el botón **Agregar SDK al proyecto seleccionado**.  
  
3.  Agregar e importar o usar sentencias en el código.  
  
    ```c#  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### C\+\+  
 En C\+\+, cree un objeto [marker\_series \(Clase\)](../profiling/marker-series-class.md) y utilícelo para llamar funciones.  La clase `marker_series` expones tres funciones para generar marcadores, el [marker\_series::write\_flag \(Método\)](../profiling/marker-series-write-flag-method.md), el [marker\_series::write\_message \(Método\)](../profiling/marker-series-write-message-method.md) y el [marker\_series::write\_alert \(Método\)](../profiling/marker-series-write-alert-method.md).  
  
##### Para agregar soporte SDK al proyecto de C\+\+ o C  
  
1.  En la barra de menús, elija **Analizar**, **Visualizador de Simultaneidad**, **Agregar SDK al proyecto**.  
  
2.  Seleccione el proyecto en el que se quiere obtener acceso al SDK y luego elija el botón **Agregar SDK al proyecto seleccionado**.  
  
3.  Para C\+\+, incluya `cvmarkersobj.h`.  Para C, incluya `cvmarkers.h`.  
  
4.  Agregar una instrucción using al código.  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Cree un objeto `marker_series` y páseselo al constructor `span`.  
  
    ```cpp  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## Uso personalizado  
 En escenarios avanzados, el SDK del Visualizador de simultaneidad expone más control.  Dos conceptos principales se asocian con escenarios más avanzados: los proveedores de marcadores y las series de marcadores.  Los proveedores de marcadores son diferentes de los proveedores ETW \(cada uno tiene una GUID diferente\).  Las series de marcadores son canales de serie de eventos que son generados por un proveedor.  Estos se pueden utilizar para organizar los eventos que son generados por un proveedor de marcadores.  
  
#### Para usar un nuevo proveedor de marcadores en un proyecto de C\# o de Visual Basic  
  
1.  Crear un objeto <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>.  El constructor toma una GUID.  
  
2.  Para registrar el proveedor, abra el cuadro de diálogo del Visualizador de Simultaneidad [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Seleccione la pestaña **Marcadores** y luego elija el botón **Agregar nuevo proveedor**.  En el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), escriba la GUID que se usó para crear el proveedor y una descripción del proveedor.  
  
#### Para utilizar un nuevo proveedor de marcadores en un proyecto de C\+\+ o C.  
  
1.  Utilice la función `CvInitProvider` para inicializar un PROVEEDOR PCV.  El constructor toma un GUID\* y un PCV\_PROVIDER\*.  
  
2.  Para registrar el proveedor, abra el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Seleccione la pestaña **Marcadores** y luego elija el botón **Agregar nuevo proveedor**.  En esta cuadro de diálogo, escriba el GUID que se utilizó para crear el proveedor y una descripción del proveedor.  
  
#### Para usar una serie de marcador en un proyecto de C\# o de Visual Basic.  
  
1.  Para utilizar un nuevo <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, primero créelo mediante un objeto <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> y luego genere marcadores de eventos directamente desde la nueva serie.  
  
    ```c#  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```vb  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### Para usar una serie de marcador en un proyecto de C\+\+  
  
1.  Crear un objeto `marker_series`.  Se pueden generar eventos desde esta nueva serie.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### Para utilizar una serie de marcador en un proyecto de C  
  
1.  Use la función `CvCreateMarkerSeries` para crear un PCV\_MARKERSERIES.  
  
    ```cpp  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Referencia de la biblioteca C\+\+](../profiling/cpp-library-reference.md)|Describe la API del Visualizador de simultaneidad para C\+\+|  
|[Referencia de la biblioteca C](../profiling/c-library-reference.md)|Describe la API del Visualizador de simultaneidad para C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Describe la API del Visualizador de simultaneidad para código administrado.|  
|[Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)|Información de referencia para las vistas y los informes de archivos de datos de generación de perfiles que se generan mediante el método de simultaneidad e incluyen datos de ejecución de subprocesos.|