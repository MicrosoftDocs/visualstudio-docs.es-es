---
title: Marcadores del Visualizador de simultaneidad | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47860775a6351cab83cd43975e94373c3558305a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54795352"
---
# <a name="concurrency-visualizer-markers"></a>Marcadores del Visualizador de simultaneidad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el visualizador de simultaneidad, los marcadores son iconos que representan los eventos que se producen en una aplicación.  Normalmente, la aplicación genera estos eventos para designar las fases o las instancias de una aplicación.  Los eventos se pueden generar mediante la aplicación o las bibliotecas y los runtimes que utiliza la aplicación.  
  
## <a name="kinds-of-markers"></a>Tipos de marcadores  
 El visualizador de simultaneidad utiliza tres tipos de marcadores para representar eventos de aplicación: marcas, mensajes e intervalos.  
  
1.  Utilice una *marca* para indicar un punto interesante de tiempo en la aplicación.  Por ejemplo, podría utilizar una marca para representar que un valor variable ha alcanzado un umbral determinado o que se produjo una excepción.  
  
2.  Un *mensaje* también marca un punto de tiempo, pero puede utilizarlo para hacer un seguimiento de estilo de registro.  Por ejemplo, lo que se podría haber volcado en un archivo de registro ahora puede encapsularlo en una llamada de mensaje para que le pueda hacer un seguimiento y verlo en el visualizador de simultaneidad. También puede utilizar el visualizador de simultaneidad para exportar estos datos a un archivo CSV.  
  
3.  Un *intervalo* representa un intervalo de tiempo en la aplicación, por ejemplo, una de sus fases.  
  
## <a name="marker-linkage-to-threads"></a>Vinculación de marcadores para los subprocesos  
 Cada subproceso que genera marcadores tiene un canal de escala de tiempo independiente.  El identificador del subproceso que es responsable de generar los eventos de marcador se muestra junto a la descripción del canal de marcador.  El identificador que se muestra en el lado izquierdo del canal de marcador coincide con el de otro subproceso en el proceso actual.  
  
## <a name="marker-importance"></a>Importancia de los marcadores  
 Los marcadores pueden tener uno de cuatro niveles de importancia: baja, normal, alta y crítica.  Los orígenes de los marcadores se pueden filtrar según el nivel de importancia.  Por ejemplo, si solo quiere ver los marcadores de un origen concreto que tenga importancia crítica o normal, puede configurar el filtro en el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md). La importancia de un marcador se muestra en la información sobre herramientas y en el [Informe de marcadores](../profiling/markers-report.md).  
  
## <a name="marker-category"></a>Categoría de los marcadores  
 Una categoría de marcador indica un grupo de eventos de marcador que proceden del mismo origen.  El visualizador de simultaneidad usa colores para distinguir las diferentes categorías de marcas e intervalos. El visualizador de simultaneidad se puede configurar para que use categorías con las que filtrar los eventos de marcador de un proveedor de eventos determinado.  Utilice el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) para configurar el filtro.  
  
## <a name="known-sources-of-markers"></a>Orígenes conocidos de marcadores  
 Cualquier proveedor de ETW puede generar marcadores, siempre y cuando el proveedor observe determinadas restricciones. Puede configurar el visualizador de simultaneidad para que escuche orígenes de eventos adicionales para los marcadores. De forma predeterminada, escucha estos orígenes de eventos:  
  
- [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)  
  
- [Biblioteca TPL](http://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23)  
  
- [Flujo de datos](http://msdn.microsoft.com/library/643575d0-d26d-4c35-8de7-a9c403e97dd6)  
  
- [Parallel LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)  
  
- [Runtime de simultaneidad](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)  
  
- [Compatibilidad con marcadores de escenario](http://msdn.microsoft.com/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
- [C++ AMP (C++ Accelerated Massive Parallelism)](http://msdn.microsoft.com/library/e27824cb-3167-409b-8c3f-a0e476d8f349)  
  
  Puede utilizar la pestaña Marcadores en el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) para controlar si los marcadores de diversos orígenes se muestran en el visualizador de simultaneidad y puede filtrar por marcadores según la importancia y la categoría.  
  
## <a name="markers-from-eventsource"></a>Marcadores de EventSource  
 El visualizador de simultaneidad también puede mostrar eventos EventSource.  Para obtener más información, consulte [Visualizar eventos EventSource como marcadores](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Vea también  
 [Marcadores de marca](../profiling/flag-markers.md)   
 [Marcadores de mensaje](../profiling/message-markers.md)   
 [Marcadores de intervalo](../profiling/span-markers.md)   
 [Visualizar eventos EventSource como marcadores](../profiling/visualizing-eventsource-events-as-markers.md)
