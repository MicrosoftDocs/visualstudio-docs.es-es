---
title: Visualizar eventos EventSource como marcadores | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c39f137299c1f229de8c3c6dc8d7329cba6033cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742554"
---
# <a name="visualizing-eventsource-events-as-markers"></a>Visualizar eventos EventSource como marcadores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El visualizador de simultaneidad puede mostrar eventos EventSource como marcadores, y puede controlar cómo se muestran los marcadores. Para ver los marcadores de EventSource, registre el GUID del proveedor de ETW mediante el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md). El visualizador de simultaneidad tiene convenciones predeterminadas para representar eventos de EventSource como [marcadores de marca](../profiling/flag-markers.md), [marcadores de intervalo](../profiling/span-markers.md) y [marcadores de mensaje](../profiling/message-markers.md). Puede personalizar cómo se muestran los eventos EventSource agregando campos personalizados a los eventos. Para obtener más información sobre los marcadores, consulte [Marcadores del visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md). Para obtener más información sobre eventos EventSource, consulte <xref:System.Diagnostics.Tracing>.  
  
## <a name="default-visualization-of-eventsource-events"></a>Visualización predeterminada de eventos EventSource  
 De forma predeterminada, el visualizador de simultaneidad usa las siguientes convenciones para representar eventos EventSource.  
  
### <a name="marker-type"></a>Tipo de marcador  
  
1.  Los eventos que tienen un [Opcode](http://msdn.microsoft.com/en-us/d97953df-669b-4c55-b1a8-925022b339b7) win:Start orwin:Stop se tratan como el principio o el final de un intervalo, respectivamente.  Los intervalos anidados o superpuestos no se pueden mostrar. Los pares de eventos que comienzan en un subproceso y acaban en otro no se pueden mostrar.  
  
2.  Un evento cuyo código de operación no es win:Start ni win:Stop se trata como una marca de marcador a menos que su [Level](http://msdn.microsoft.com/en-us/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) (campo de EVENT_RECORD.EVENT_HEADER.EVENT_DESCRIPTOR) sea win:Verbose o superior.  
  
3.  En los demás casos, el evento se trata como un mensaje.  
  
### <a name="importance"></a>Importancia  
 La siguiente tabla define cómo se asigna el nivel de evento a la importancia de marcador.  
  
|Nivel ETW|Importancia del visualizador de simultaneidad|  
|---------------|---------------------------------------|  
|win:LogAlways|Normal|  
|win:Critical|Crítico|  
|win:Error|Crítico|  
|win:Warning|Alto|  
|win:Informational|Normal|  
|win:Verbose|Bajo|  
|Mayor que win:verbose|Bajo|  
  
### <a name="series-name"></a>Nombre de serie  
 El nombre de la tarea del evento se usa para el nombre de la serie. El nombre de la serie está vacío si no se definió ninguna tarea para el evento.  
  
### <a name="category"></a>Categoría  
 Si el Level es win:Critical o win:Error, la categoría es Alert (-1). De lo contrario, la categoría es el valor predeterminado (0).  
  
### <a name="text"></a>Texto  
 Si se definió para el evento un mensaje de texto con formato de tipo printf, se muestra como la descripción del marcador. De lo contrario, la descripción es el nombre del evento y el valor de cada campo de carga.  
  
## <a name="customizing-visualization-of-eventsource-events"></a>Personalizar la visualización de eventos EventSource  
 Puede personalizar cómo se muestran los eventos EventSource agregando los campos correspondientes al evento, tal como se describe en las siguientes secciones.  
  
### <a name="marker-type"></a>Tipo de marcador  
 Utilice el campo `cvType`, un byte, para controlar el tipo de marcador que se usa para representar el evento. Estos son los valores disponibles para cvType:  
  
|Valor cvType|Tipo de marcador resultante|  
|------------------|---------------------------|  
|0|Mensaje|  
|1|Inicio de intervalo|  
|2|Final de intervalo|  
|3|Marcar|  
|Todos los demás valores|Mensaje|  
  
### <a name="importance"></a>Importancia  
 Puede usar el campo `cvImportance`, un byte, para controlar la configuración de la importancia de un evento EventSource. Sin embargo, se recomienda controlar la importancia mostrada de un evento mediante su Level.  
  
|Valor cvImportance|Importancia del visualizador de simultaneidad|  
|------------------------|---------------------------------------|  
|0|Normal|  
|1|Crítico|  
|2|Alto|  
|3|Alto|  
|4|Normal|  
|5|Bajo|  
|Todos los demás valores|Bajo|  
  
### <a name="series-name"></a>Nombre de serie  
 Utilice el campo de evento `cvSeries`, una cadena, para controlar el nombre de la serie que el visualizador de simultaneidad proporciona a un evento EventSource.  
  
### <a name="category"></a>Categoría  
 Utilice el campo `cvCategory`, un byte, para controlar la categoría que el visualizador de simultaneidad proporciona a un evento EventSource.  
  
### <a name="text"></a>Texto  
 Utilice el campo `cvTextW`, una cadena, para controlarla descripción que el visualizador de simultaneidad proporciona a un evento EventSource.  
  
### <a name="spanid"></a>SpanID  
 Utilice el campo cvSpanId, un número entero, para hacer coincidir los pares de eventos. El valor para cada par de eventos de inicio y detención que representan un intervalo debe ser único. Normalmente, para código simultáneo esto requiere el uso de primitivos de sincronización, como <xref:System.Threading.Interlocked.Exchange%2A>, para garantizar que la clave (el valor que se usa para CvSpanID) es correcta.  
  
> [!NOTE]
>  Para usar SpanID para anidar intervalos, permita que se superpongan en el mismo subproceso o no permita que se inicien en un subproceso terminen en otro.  
  
## <a name="see-also"></a>Vea también  
 [Marcadores del visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md)



