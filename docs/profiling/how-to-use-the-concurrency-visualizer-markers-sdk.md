---
title: Usar el SDK de marcadores del Visualizador de simultaneidad | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cf33ad094716ee0f8f4c8cc4bb06220db1237e5
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851585"
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Cómo Usar el SDK de marcadores del Visualizador de simultaneidad
Este tema muestra cómo usar el SDK del visualizador de simultaneidad para crear intervalos y escribir marcas, mensajes y alertas.

### <a name="to-use-c"></a>Para usar C++

1. Agregue compatibilidad con el SDK del visualizador de simultaneidad a la aplicación. Para obtener más información, consulte [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md).

2. Agregue una instrucción `include` y una instrucción `using` para el SDK.

    ```cpp
    #include <cvmarkersobj.h>
    using namespace Concurrency::diagnostic;
    ```

3. Agregue código para crear tres intervalos en la serie del marcador predeterminado y escriba una marca, un mensaje y una alerta para cada intervalo. Los métodos para escribir marcas, mensajes y alertas son miembros de la clase [marker_series](../profiling/marker-series-class.md). El constructor para la clase [span](../profiling/span-class.md) requiere un objeto `marker_series`, para que cada intervalo esté asociado a una serie de marcadores específica. Un `span` finaliza cuando se elimina.

    ```cpp
    marker_series series;
    span *flagSpan = new span(series, 1, _T("flag span"));
    series.write_flag(_T("Here is the flag."));
    delete flagSpan;

    span *messageSpan = new span(series, 2, _T("message span"));
    series.write_flag(_T("Here is the message."));
    delete messageSpan;

    span *alertSpan = new span(series, 3, _T("alert span"));
    series.write_flag(_T("Here is the alert."));
    delete alertSpan;
    ```

4. En la barra de menús, elija **Analizar**, **Visualizador de simultaneidad**, **Comenzar con el proyecto actual** para ejecutar la aplicación y mostrar el visualizador de simultaneidad. La siguiente ilustración muestra los tres intervalos y tres marcadores en el visualizador de simultaneidad.

     ![Visualizador de simultaneidad con tres marcadores y alertas](../profiling/media/cvmarkersnative.png "CvMarkersNative")

5. Agregue código para crear series de marcadores personalizadas adicionales llamando al constructor de `marker_series` que toma un nombre de cadena para la serie de marcadores.

    ```cpp
    marker_series flagSeries(_T("flag series"));
    span *flagSeriesSpan = new span(flagSeries, 1, _T("flag span"));
    flagSeries.write_flag(1, _T("flag"));
    // Sleep to even out the display in the Concurrency Visualizer.
    Sleep(50);
    delete flagSeriesSpan;

    marker_series messageSeries(_T("message series"));
    span *messageSeriesSpan = new span(messageSeries, 1, _T("message span"));
    messageSeries.write_message(1, _T("message"));
    // Sleep to even out the display in the Concurrency Visualizer.
    Sleep(50);
    delete messageSeriesSpan;
    ```

6. Inicie el proyecto actual para mostrar el visualizador de simultaneidad. La serie de dos marcadores aparece en sus propios canales en la vista Subprocesos. En la siguiente ilustración se muestran dos nuevos intervalos.

     ![Visualizador de simultaneidad con tres series de marcadores personalizados](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")

### <a name="to-use-visual-basic-or-c"></a>Para usar Visual Basic o C\#

1. Agregue compatibilidad con el SDK del visualizador de simultaneidad a la aplicación. Para obtener más información, consulte [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md).

2. Agregue una instrucción `using` o `Imports` para el SDK.

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

3. Agregue código para crear tres intervalos en la serie de marcadores predeterminada y escriba una marca, un mensaje y una alerta para cada intervalo. Cree un objeto [Span](/previous-versions/hh694189(v=vs.140)) llamando al método `EnterSpan` estático. Para escribir en la serie predeterminada, use los métodos de escritura estáticos de la clase [Markers](/previous-versions/hh694099(v=vs.140)).

    ```vb
    Dim flagSpan As Span = Markers.EnterSpan("flag span")
    Markers.WriteFlag("Here is the flag.")
    flagSpan.Leave()

    Dim messageSpan As Span = Markers.EnterSpan("message span")
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1)
    Markers.WriteMessage("Here is a message")
    messageSpan.Leave()

    Dim alertSpan As Span = Markers.EnterSpan("alert span")
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1)
    Markers.WriteAlert("Here is an alert")
    alertSpan.Leave()
    ```

    ```csharp
    Span flagSpan = Markers.EnterSpan("flag span");
    Markers.WriteFlag("Here is the flag.");
    flagSpan.Leave();

    Span messageSpan = Markers.EnterSpan("message span");
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1);
    Markers.WriteMessage("Here is a message");
    messageSpan.Leave();

    Span alertSpan = Markers.EnterSpan("alert span");
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1);
    Markers.WriteAlert("Here is an alert");
    alertSpan.Leave();
    ```

4. En la barra de menús, elija **Analizar**, **Visualizador de simultaneidad**, **Comenzar con el proyecto actual** para ejecutar la aplicación y mostrar el visualizador de simultaneidad. La siguiente ilustración muestra los tres intervalos y tres marcadores de la vista Subprocesos del Visualizador de simultaneidad.

     ![Visualizador de simultaneidad con marcadores y alertas](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")

5. Agregue código para crear series de marcadores de cliente con el método [CreateMarkerSeries](/previous-versions/hh694171(v=vs.140)) estático. La clase [MarkerSeries](/previous-versions/hh694127(v=vs.140)) contiene métodos para crear intervalos y escribir marcas, mensajes y alertas.

    ```VB

    Dim flagSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series")
    Dim flagSeriesSpan As Span = flagSeries.EnterSpan("flag span")
    System.Threading.Thread.Sleep(1)
    flagSeries.WriteFlag(1, "flag")
    System.Threading.Thread.Sleep(1)
    flagSeriesSpan.Leave()

    Dim messageSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("message series")
    Dim messageSeriesSpan As Span = messageSeries.EnterSpan("message span")
    messageSeries.WriteMessage("message")
    System.Threading.Thread.Sleep(1)
    messageSeriesSpan.Leave()
    ```

    ```csharp

    MarkerSeries flagSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series");
    Span flagSeriesSpan = flagSeries.EnterSpan("flag span");
    System.Threading.Thread.Sleep(1);
    flagSeries.WriteFlag(1, "flag");
    System.Threading.Thread.Sleep(1);
    flagSeriesSpan.Leave();

    MarkerSeries messageSeries = Markers.DefaultWriter.CreateMarkerSeries("message series");
    Span messageSeriesSpan = messageSeries.EnterSpan("message span");
    messageSeries.WriteMessage("message");
    System.Threading.Thread.Sleep(1);
    messageSeriesSpan.Leave();
    ```

6. Inicie el proyecto actual para mostrar el visualizador de simultaneidad. Las tres series de marcadores aparecen en sus propios canales en la vista Subprocesos. En la siguiente ilustración se muestran tres nuevos intervalos.

     ![Visualizador de simultaneidad con tres series de marcadores personalizados](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")

## <a name="see-also"></a>Vea también
- [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)
