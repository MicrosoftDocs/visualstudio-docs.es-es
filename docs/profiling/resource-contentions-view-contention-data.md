---
title: 'Vista Contenciones del recurso: datos de contención | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57fc5075ee375ed73b448e8a90e8bb2c3e22e7bf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970817"
---
# <a name="resource-contentions-view---contention-data"></a>Vista Contenciones del recurso: datos de contención
La vista Contenciones del recurso muestra datos de contención de recursos que son el origen de eventos de contención. Un evento de contención se produce cuando una función en un subproceso se ve obligada a esperar para obtener acceso al recurso porque una función en otro subproceso ha adquirido acceso exclusivo al recurso. Cada recurso es el nodo raíz de un árbol de llamadas que muestra las rutas de ejecución de la función que dieron lugar a los eventos de contención.  
  
## <a name="data-values"></a>Valores de datos  
  
### <a name="resource-values"></a>Valores de recursos  
 Los datos de una fila de recurso muestran el tiempo total que se ha bloqueado el acceso al recurso en los datos de generación de perfiles y el número total de eventos de contención que se produjeron debido a conflictos de acceso a este recurso. Los valores inclusivos y exclusivos para un recurso son siempre los mismos.  
  
### <a name="function-values"></a>Valores de función  
 Los valores de función se basan en las instancias de la función que se produjeron en la ruta de acceso de ejecución representada en el árbol de llamadas.  
  
-   Los valores exclusivos se basan en los eventos que se produjeron cuando la función estaba ejecutando instrucciones en el cuerpo de la función. Los eventos que se produjeron en funciones a las que llamó la función no se incluyen en los valores exclusivos.  
  
-   Los valores inclusivos se basan en los eventos que se produjeron cuando la función o una función a la que llamó la función se estaba ejecutando.  
  
### <a name="percentage-values"></a>Valores de porcentaje  
 Los valores de porcentaje se basan en los eventos de contención o el tiempo total de los datos de generación de perfiles. Si se filtra el informe o la vista de la generación de perfiles, solo se usa el tiempo bloqueado y las contenciones de los datos filtrados como valor total.  
  
## <a name="navigating-the-resource-allocation-view"></a>Navegar por la vista Asignación de recursos  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Name**|El nombre del recurso o la función.|  
|**Tiempo de bloqueo exclusivo**|-   Para un recurso, el tiempo total durante el que se ha bloqueado el acceso al recurso y que produjo que un subproceso tuviese que esperar.<br />-   En una función, el tiempo durante el que se ha bloqueado el acceso de estas instancias de la función al recurso primario cuando la función estaba ejecutando código en el cuerpo de la función. No se incluye el tiempo de bloqueo de las funciones a las que llamó la función.|  
|**Porcentaje de tiempo de bloqueo exclusivo**|-   Para un recurso, el porcentaje de tiempo de bloqueo total de los datos de generación de perfiles que es tiempo de bloqueo de este recurso<br />-   Para una función, el porcentaje de tiempo de bloqueo total de los datos de generación de perfiles que es tiempo de bloqueo exclusivo de estas instancias de recurso.|  
|**Contenciones exclusivas**|-   Para un recurso, el número total de veces durante las que se ha bloqueado el acceso al recurso y que produjo que un subproceso tuviese que esperar.<br />-   En una función, el número total de veces durante las que se ha bloqueado el acceso de estas instancias de la función al recurso primario cuando la función estaba ejecutando código en el cuerpo de la función. No se incluye los eventos de bloqueo de las funciones a las que llamó la función.|  
|**Porcentaje de contenciones exclusivas**|-   Para un recurso, el porcentaje de todos los eventos de contención de los datos de generación de perfiles que eran eventos de contención para el acceso a este recurso.<br />-   Para una función, el porcentaje de todos los eventos de contención de los datos de generación de perfiles que eran eventos de contención exclusivos de las instancias de esta función para el recurso principal.|  
|**Tiempo de bloqueo inclusivo**|-   Para un recurso, el tiempo total durante el que se ha bloqueado el acceso al recurso y que produjo que un subproceso tuviese que esperar.<br />-   En una función, el tiempo durante el que se ha bloqueado el acceso de estas instancias de la función, o cualquier función llamada por las instancias, al recurso primario cuando la función estaba ejecutando código en el cuerpo de la función.|  
|**Porcentaje de tiempo de bloqueo inclusivo**|-   Para un recurso, el porcentaje de tiempo de bloqueo total de los datos de generación de perfiles que es tiempo de bloqueo de este recurso<br />-   Para una función, el porcentaje de tiempo de bloqueo total de la generación de perfiles que es tiempo de bloqueo inclusivo de estas instancias de recurso.|  
|**Contenciones inclusivas**|-   Para un recurso, el número total de veces durante las que se ha bloqueado el acceso al recurso y que produjo que un subproceso tuviese que esperar.<br />-   Para una función, el porcentaje de todos los eventos de contención de la generación de perfiles que eran eventos de contención inclusivos de las instancias de esta función para el recurso principal.|  
|**Porcentaje de contenciones inclusivas**|-   Para un recurso, el porcentaje de todos los eventos de contención de la generación de perfiles que eran eventos de contención para el acceso a este recurso.<br />-   En una función, el número total de veces durante las que se ha bloqueado el acceso de estas instancias de la función al recurso primario cuando la función estaba ejecutando código en el cuerpo de la función. No se incluye los eventos de bloqueo de las funciones a las que llamó la función.|  
|**Nivel**|La profundidad de esta función en el árbol de llamadas. Solo disponible en los informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Identificador del proceso**|El Id. del proceso (PID) en el que se estaba ejecutando la función.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|