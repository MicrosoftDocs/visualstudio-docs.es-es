---
title: SDK del visualizador de simultaneidad | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c02959f30f89b8f7c79527026404099a4452a827
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691191"
---
# <a name="concurrency-visualizer-sdk"></a>SDK del Visualizador de simultaneidad
Puede instrumentar el código fuente mediante el uso del SDK del visualizador de simultaneidad para mostrar información adicional en el visualizador de simultaneidad. Puede asociar los datos adicionales a fases y eventos en el código. Estas visualizaciones adicionales se denominan *marcadores*.  Para obtener un tutorial de introducción, consulte [Introducción al SDK del visualizador de simultaneidad](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## <a name="properties"></a>Propiedades  
 Las marcas, los intervalos y los mensajes tienen dos propiedades: categoría e importancia. En el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), puede utilizar estas propiedades para filtrar el conjunto de marcadores que se muestran. Además, estas propiedades afectan a la representación visual de los marcadores. Por ejemplo, el tamaño de las marcas se utiliza para representar la importancia. Además, el color se utiliza para indicar la categoría.  
  
## <a name="basic-usage"></a>Uso básico  
 El visualizador de simultaneidad expone un proveedor predeterminado que se puede utilizar para generar marcadores. El proveedor ya está registrado con el visualizador de simultaneidad, y no es necesario hacer nada más para que los marcadores aparezcan en la interfaz de usuario.  
  
### <a name="c-and-visual-basic"></a>C# y Visual Basic  
 En C#, Visual Basic y otro código administrado, use el proveedor predeterminado llamando a <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>. Expone cuatro funciones para generar marcadores: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A> y <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>. Existen varias sobrecargas de estas funciones, según si quiere utilizar valores predeterminados para las propiedades.  La sobrecarga más simple toma solo un parámetro de cadena que especifica la descripción del evento. La descripción se muestra en los informes del visualizador de simultaneidad.  
  
##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Para agregar compatibilidad con SDK a un proyecto de C# o Visual Basic  
  
1.  En la barra de menús, elija **Analizar**, **Visualizador de simultaneidad** y **Agregar SDK al proyecto**.  
  
2.  Seleccione el proyecto en el que desea tener acceso al SDK y, a continuación, elija el botón **Agregar SDK al proyecto seleccionado**.  
  
3.  Agregue una instrucción imports o using al código.  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```VB  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### <a name="c"></a>C++  
 En C++, cree un objeto [marker_series (clase)](../profiling/marker-series-class.md) y utilícelo para llamar a funciones.  La clase `marker_series` expone tres funciones para generar marcadores: [marker_series:: write_flag (método)](../profiling/marker-series-write-flag-method.md), [marker_series:: write_message (método)](../profiling/marker-series-write-message-method.md) y [marker_series:: write_alert (método)](../profiling/marker-series-write-alert-method.md).  
  
##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Para agregar compatibilidad con SDK a un proyecto de C++ o C  
  
1.  En la barra de menús, elija **Analizar**, **Visualizador de simultaneidad** y **Agregar SDK al proyecto**.  
  
2.  Seleccione el proyecto en el que desea tener acceso al SDK y, a continuación, elija el botón **Agregar SDK al proyecto seleccionado**.  
  
3.  Para C++, incluya `cvmarkersobj.h`. Para C++, incluya `cvmarkers.h`.  
  
4.  Agregue una instrucción using al código.  
  
    ```cpp  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Cree un objeto `marker_series` y páselo al constructor `span`.  
  
    ```C++  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## <a name="custom-usage"></a>Uso personalizado  
 Para escenarios avanzados, el SDK del visualizador de simultaneidad muestra un mayor control.  Dos conceptos principales están asociados a escenarios más avanzados: los proveedores de marcadores y las series de marcadores. Los proveedores de marcadores son proveedores ETW diferentes (cada uno tiene un GUID diferente). Las series de marcadores son canales en serie de eventos generados por un proveedor. Puede utilizarlas para organizar los eventos generados por un proveedor de marcadores.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Para utilizar un nuevo proveedor de marcadores en un proyecto de C# o Visual Basic  
  
1.  Crear un objeto <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>.  El constructor toma un GUID.  
  
2.  Para registrar el proveedor, abra el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) del visualizador de simultaneidad.  Seleccione la pestaña **Marcadores** y, a continuación, elija el botón **Agregar un nuevo proveedor**. En el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md), escriba el GUID que se utilizó para crear el proveedor y una descripción del proveedor.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Para utilizar un nuevo proveedor de marcadores en un proyecto de C++ o C  
  
1.  Use la función `CvInitProvider` para inicializar un PCV_PROVIDER.  El constructor toma un GUID* y PCV_PROVIDER\*.  
  
2.  Para registrar el proveedor, abra el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) del visualizador de simultaneidad.  Seleccione la pestaña **Marcadores** y, a continuación, elija el botón **Agregar un nuevo proveedor**. En este cuadro de diálogo, escriba el GUID que se utilizó para crear el proveedor y una descripción del proveedor.  
  
#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Para usar una serie de marcadores en un proyecto de C# o Visual Basic  
  
1.  Para usar un nuevo <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries>, primero créelo mediante un objeto <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter> y, después, genere eventos de marcador directamente desde la nueva serie.  
  
    ```csharp  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");  
    series1.WriteFlag("My flag");  
    ```  
  
    ```VB  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")  
    series1.WriteFlag("My flag")  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Para usar una serie de marcadores en un proyecto de C++  
  
1.  Crear un objeto `marker_series`.  Puede generar eventos de esta nueva serie.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Para usar una serie de marcadores en un proyecto de C  
  
1.  Utilice la función `CvCreateMarkerSeries` para crear una PCV_MARKERSERIES.  
  
    ```C++  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## <a name="see-also"></a>Vea también  
  
|Title|Description|  
|-----------|-----------------|  
|[Referencia de la biblioteca de C++](../profiling/cpp-library-reference.md)|Describe la API del visualizador de simultaneidad de C++.|  
|[Referencia de la biblioteca de C](../profiling/c-library-reference.md)|Describe la API del visualizador de simultaneidad de C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Describe la API del visualizador de simultaneidad del código administrado.|  
|[Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)|Información de referencia para las vistas y los informes de archivos de datos de generación de perfiles generados mediante el método de simultaneidad y que incluyen datos de ejecución de subprocesos.|