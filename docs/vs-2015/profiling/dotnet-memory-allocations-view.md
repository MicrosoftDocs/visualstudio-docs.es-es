---
title: Vista de asignaciones de memoria de .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a3c24d8aa984ddc947d3c532020974a196192940
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179064"
---
# <a name="net-memory-allocations-view"></a>Vista de asignaciones de memoria de .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista de asignaciones enumera los tipos que se han creado durante la generación de perfiles. Cada tipo es el nodo raíz de un árbol de llamadas que muestra las rutas de ejecución de la función que dieron lugar a las asignaciones del tipo.  
  
 Los datos en una fila de tipo muestran el número total de objetos del tipo que se han creado en la generación de perfiles y el número total de bytes asignados a los objetos de ese tipo. Los valores inclusivos y exclusivos de un tipo son siempre los mismos.  
  
- Los valores inclusivos corresponden a los objetos creados en las instancias de la función y sus funciones secundarias a las que llamó la función primaria en el árbol de llamadas.  
  
- Los valores exclusivos corresponden a los objetos que la función creó directamente cuando la función primaria los llamó. No se incluyen los objetos creados en funciones secundarias.  
  
  Los datos de una función muestran el número de objetos creados y el número de bytes asignados a objetos del tipo primario.  
  
## <a name="highlighting-the-execution-hot-path"></a>Resaltar la ruta de acceso activa de ejecución  
 Puede encontrar la ruta de acceso de ejecución del árbol de llamadas que ha creado la mayoría de los objetos del tipo primario.  
  
- Para mostrar la ruta de acceso más activa, haga clic con el botón derecho en el tipo o función y, a continuación, haga clic en **Expandir ruta de acceso activa**.  
  
|Columna|DESCRIPCIÓN|  
|------------|-----------------|  
|**Nombre**|Nombre del tipo o función asignado.|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Nombre del módulo**|Nombre del módulo que contiene el tipo o la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene el tipo o la función.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición del tipo o de la función.|  
|**Número de línea de la función**|Número de línea del inicio de la definición de este tipo o de la función en el archivo de origen.|  
|**Nivel**|Indica si los datos son para un tipo o una función.|  
|**Asignaciones inclusivas**|-   Para una función, el número total de objetos del tipo primario que la función ha creado. Este número incluye los objetos creados en funciones secundarias.<br />-   Para un tipo, el número total de instancias de ese tipo que se han creado.|  
|**Porcentaje de asignaciones inclusivas**|-   Para una función, el porcentaje de todos los objetos creados en la generación de perfiles que eran asignaciones inclusivas del tipo primario por parte de la función.<br />-   Para un tipo, el porcentaje del número total de objetos creados en la generación de perfiles que eran instancias del tipo.|  
|**Asignaciones exclusivas**|-   Para una función, el número de objetos creados cuando la función se estaba ejecutando directamente en la parte superior de la pila de llamadas. Este número no incluye los objetos creados en funciones secundarias.<br />-   Para un tipo, el número total de instancias de ese tipo que se han creado.|  
|**Porcentaje de asignaciones exclusivas**|-   Para una función, el porcentaje de todos los objetos creados en la generación de perfiles que eran asignaciones exclusivas del tipo primario por parte de la función.<br />-   Para un tipo, el porcentaje del número total de objetos creados en la generación de perfiles que eran instancias del tipo.|  
|**Porcentaje de bytes inclusivos**|-   Para una función, el número de bytes de memoria que la función ha asignado para objetos del tipo primario. Este número incluye la memoria que sus funciones secundarias han asignado.<br />-   Para un tipo, el número total de bytes asignados en la generación de perfiles para las instancias del tipo.|  
|**Porcentaje de bytes inclusivos**|-   Para una función, el porcentaje de toda la memoria asignada en la generación de perfiles que eran asignaciones inclusivas del tipo primario por parte de la función.<br />-   Para un tipo, el porcentaje de toda la memoria asignada en la generación de perfiles que se ha asignado para las instancias del tipo.|  
|**Bytes exclusivos**|-   Para una función, el número de bytes de memoria que la función ha asignado para objetos del tipo primario. Este número no incluye la memoria que sus funciones secundarias han asignado.<br />-   Para un tipo, el número total de bytes asignados en la generación de perfiles para las instancias del tipo.|  
|**Porcentaje de bytes exclusivos**|-   Para una función, el porcentaje de toda la memoria asignada en la generación de perfiles que eran asignaciones exclusivas del tipo primario por parte de la función.<br />-   Para un tipo, el porcentaje de toda la memoria asignada en la generación de perfiles que se ha asignado para las instancias del tipo.|
