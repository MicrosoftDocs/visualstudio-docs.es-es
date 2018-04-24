---
title: Descripción de los valores de datos de contención de recursos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdc41ee4c3c9f53d45245c6c305d7f8e221757f4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="understanding-resource-contention-data-values"></a>Descripción de los valores de datos de contención de recursos

La generación de perfiles de contención de recursos recopila información detallada de la pila de llamadas cada vez que subprocesos competidores en una aplicación se ven obligados a esperar para obtener acceso a un recurso compartido.

Los informes de contención de recursos muestran el número total de contenciones y el tiempo total invertido esperando a un recurso por los módulos, funciones, líneas del código fuente e instrucciones en los que se produjo la espera.

- Los valores inclusivos muestran el número total de contenciones que obligan a una función a esperar por las contenciones de recursos y el tiempo total de espera de la función.  Las contenciones originadas por funciones secundarias llamadas por la función se incluyen en los valores inclusivos.

- Los valores exclusivos muestran solo el número de contenciones que obligan a una función a esperar y que están causadas por el código en el cuerpo de la función. No se incluyen las contenciones producidas por funciones secundarias. El tiempo exclusivo de la función también incluye los tiempos de espera producidos por instrucciones del cuerpo de la función.

Las vistas de informes de contención de recursos también incluyen gráficos de escala de tiempo que se muestran los eventos de contención individuales a lo largo del tiempo y muestran las pilas de llamadas que crearon el evento concreto. Para obtener más información, consulte uno de los temas siguientes:

- [Vista Detalles del subproceso](../profiling/thread-details-view-contention-data.md)

- [Vista Detalles de recursos](../profiling/resource-details-view-contention-data.md)

Para obtener más información sobre el segundo modo de generación de perfiles de simultaneidad, consulte [visualizador de simultaneidad](../profiling/concurrency-visualizer.md).