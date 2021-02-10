---
title: Marcadores del Visualizador de simultaneidad | Microsoft Docs
description: 'Obtenga más información sobre los marcadores en el visualizador de simultaneidad. Los marcadores son iconos que representan eventos generados por una aplicación. Hay tres tipos: marcas, mensajes e intervalos.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3ff013f546393447b8303575489164a3a7be00a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941143"
---
# <a name="concurrency-visualizer-markers"></a>Marcadores del Visualizador de simultaneidad
En el visualizador de simultaneidad, los marcadores son iconos que representan los eventos que se producen en una aplicación.  Normalmente, la aplicación genera estos eventos para designar las fases o las instancias de una aplicación.  Los eventos se pueden generar mediante la aplicación o las bibliotecas y los runtimes que utiliza la aplicación.

## <a name="kinds-of-markers"></a>Tipos de marcadores
 El visualizador de simultaneidad utiliza tres tipos de marcadores para representar eventos de aplicación: marcas, mensajes e intervalos.

1. Utilice una *marca* para indicar un punto interesante de tiempo en la aplicación.  Por ejemplo, podría utilizar una marca para representar que un valor variable ha alcanzado un umbral determinado o que se produjo una excepción.

2. Un *mensaje* también marca un punto de tiempo, pero puede utilizarlo para hacer un seguimiento de estilo de registro.  Por ejemplo, lo que se podría haber volcado en un archivo de registro ahora puede encapsularlo en una llamada de mensaje para que le pueda hacer un seguimiento y verlo en el visualizador de simultaneidad. También puede utilizar el visualizador de simultaneidad para exportar estos datos a un archivo CSV.

3. Un *intervalo* representa un intervalo de tiempo en la aplicación, por ejemplo, una de sus fases.

## <a name="marker-linkage-to-threads"></a>Vinculación de marcadores para los subprocesos
 Cada subproceso que genera marcadores tiene un canal de escala de tiempo independiente.  El identificador del subproceso que es responsable de generar los eventos de marcador se muestra junto a la descripción del canal de marcador.  El identificador que se muestra en el lado izquierdo del canal de marcador coincide con el de otro subproceso en el proceso actual.

## <a name="marker-importance"></a>Importancia de los marcadores
 Los marcadores pueden tener uno de cuatro niveles de importancia: baja, normal, alta y crítica.  Los orígenes de los marcadores se pueden filtrar según el nivel de importancia.  Por ejemplo, si solo quiere ver los marcadores de un origen concreto que tenga importancia crítica o normal, puede configurar el filtro en el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md). La importancia de un marcador aparece en la información sobre herramientas y en el [informe Marcadores](../profiling/markers-report.md).

## <a name="marker-category"></a>Categoría de los marcadores
 Una categoría de marcador indica un grupo de eventos de marcador que proceden del mismo origen.  El visualizador de simultaneidad usa colores para distinguir las diferentes categorías de marcas e intervalos. El visualizador de simultaneidad se puede configurar para que use categorías con las que filtrar los eventos de marcador de un proveedor de eventos determinado.  Utilice el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) para configurar el filtro.

## <a name="known-sources-of-markers"></a>Orígenes conocidos de marcadores
 Cualquier proveedor de ETW puede generar marcadores, siempre y cuando el proveedor observe determinadas restricciones. Puede configurar el visualizador de simultaneidad para que escuche orígenes de eventos adicionales para los marcadores. De forma predeterminada, escucha estos orígenes de eventos:

- [SDK del visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md)

- [Biblioteca TPL](/dotnet/standard/parallel-programming/task-parallel-library-tpl)

- [Flujo de datos](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)

- [Parallel LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)

- [Runtime de simultaneidad](/cpp/parallel/concrt/concurrency-runtime)

- [Compatibilidad con marcadores de escenario](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))

- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)

  Puede utilizar la pestaña Marcadores en el cuadro de diálogo [Configuración avanzada](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) para controlar si los marcadores de diversos orígenes se muestran en el visualizador de simultaneidad y puede filtrar por marcadores según la importancia y la categoría.

## <a name="markers-from-eventsource"></a>Marcadores de EventSource
 El visualizador de simultaneidad también puede mostrar eventos EventSource.  Para obtener más información, vea [Visualizar eventos EventSource como marcadores](../profiling/visualizing-eventsource-events-as-markers.md).

## <a name="see-also"></a>Consulte también
- [Marcadores de marca](../profiling/flag-markers.md)
- [Marcadores de mensaje](../profiling/message-markers.md)
- [Marcadores de intervalo](../profiling/span-markers.md)
- [Visualizar eventos EventSource como marcadores](../profiling/visualizing-eventsource-events-as-markers.md)