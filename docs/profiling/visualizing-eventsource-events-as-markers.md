---
title: "Visualizar eventos EventSource como marcadores | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizar eventos EventSource como marcadores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Visualizador de simultaneidad puede mostrar eventos EventSource como marcadores y se puede controlar cómo se muestran los marcadores.  Para ver los marcadores EventSource, registre la GUID del proveedor ETW mediante el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  El Visualizador de simultaneidad tiene convenciones predeterminadas para representar eventos EventSource como [Marcadores de marca](../profiling/flag-markers.md), [Marcadores de intervalo](../profiling/span-markers.md) y [Marcadores de mensaje](../profiling/message-markers.md).  Se puede personalizar cómo se muestran los eventos EventSource agregando campos personalizados a los eventos.  Para obtener más información sobre los marcadores, consulte [Marcadores del Visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md).  Para obtener más información sobre los eventos EventSourcce, consulte <xref:System.Diagnostics.Tracing>.  
  
## Visualización predeterminada de eventos EventSource  
 De forma predeterminada, el Visualizador de simultaneidad usa las siguientes convenciones para representar los eventos EventSource.  
  
### Tipo de marcador  
  
1.  Los eventos que tienen [Opcode](http://msdn.microsoft.com/es-es/d97953df-669b-4c55-b1a8-925022b339b7) win:Start o win:Stop se tratan como el principio o el fin de un periodo, respectivamente.  Los periodos anidados o solapados no se pueden mostrar.  Los pares de eventos que comienzan en un subproceso y terminan en otro no se pueden mostrar.  
  
2.  Un evento cuyo Opcode no es ni win:Start ni win:Stop se trata como una marca de marcador a menos que su [Nivel](http://msdn.microsoft.com/es-es/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) \(campo de EVENT\_RECORD.EVENT\_HEADER.EVENT\_DESCRIPTOR\) sea win:Verbose o mayor.  
  
3.  En todos los demás casos, el evento se trata como un mensaje.  
  
### Importancia  
 En la tabla siguiente se define cómo asigna el nivel del evento la importancia del marcador.  
  
|Nivel ETW|Importancia del Visualizador de simultaneidad.|  
|---------------|----------------------------------------------------|  
|win:LogAlways|Normal|  
|win:Critical|Crítica|  
|win:Error|Crítica|  
|win:Warning|High|  
|win:Informational|Normal|  
|win:Verbose|Low|  
|Mayor que win:verbose|Low|  
  
### El nombre de la serie.  
 El nombre de la tarea del evento se usa para el nombre de la serie.  El nombre de la serie está vacío si no se definió ninguna tarea para el evento.  
  
### Categoría  
 Si el nivel es win:Critical o win:Error, entonces la categoría es Alert \(\-1\).  De lo contrario, la categoría es la predeterminada \(0\).  
  
### Texto  
 Si un mensaje de texto con formato de tipo printf se definió para el evento, se muestra como una descripción del marcador.  De lo contrario, la descripción es el nombre del evento y el valor de cada campo de carga.  
  
## Personalizar la visualización de los eventos EventSource  
 Se puede personalizar cómo se muestran los eventos EventSource añadiendo los campos apropiados al evento, como se describe en las siguientes secciones.  
  
### Tipo de marcador  
 Use el campo `cvType`, un byte, para controlar el tipo de marcador que se usa para representar el evento.  Los valores disponibles para estos cvType::  
  
|Valor de cvType|Tipo de marcador resultante|  
|---------------------|---------------------------------|  
|0|Mensaje|  
|1|Periodo principal|  
|2|Periodo final|  
|3|Marcar|  
|Todos los demás valores|Mensaje|  
  
### Importancia  
 Se puede usar el campo `cvImportance`, un byte, para controlar la configuración más importante para un evento EventSource.  Sin embargo, se recomienda que se controle la importancia mostrada de un evento mediante su nivel.  
  
|Valor cvImportance|Importancia del Visualizador de simultaneidad.|  
|------------------------|----------------------------------------------------|  
|0|Normal|  
|1|Crítica|  
|2|High|  
|3|High|  
|4|Normal|  
|5|Low|  
|Todos los demás valores|Low|  
  
### El nombre de la serie.  
 Use el campo de evento `cvSeries`, una cadena, para controlar el nombre de la serie que el Visualizador de simultaneidad da a un evento EventSource.  
  
### Categoría  
 Use el campo `cvCategory`, un byte, para controlar la categoría que el Visualizador de simultaneidad da a un evento EventSource.  
  
### Texto  
 Use el campo `cvTextW`, una cadena, para controlar la descripción que el Visualizador de simultaneidad da a un evento EventSource.  
  
### SpanID  
 Use el campo cvSpanID, un entero, para enlazar pares de eventos.  El valor para cada par de eventos inicio\/parada que representan un periodo debe ser único.  Normalmente para código concurrente, esto requiere el uso de primitivas de sincronización como <xref:System.Threading.Interlocked.Exchange%2A> para asegurar que la clave \(el valor que se usa para CvSpanID\) es correcta.  
  
> [!NOTE]
>  El uso de SpanID para anidar periodos, que les permite solaparse parcialmente en el mismo subproceso, o les permite empezar en un subproceso y terminar en otro, no está admitido.  
  
## Vea también  
 [Marcadores del Visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md)