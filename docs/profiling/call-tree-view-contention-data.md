---
title: 'Vista Árbol de llamadas: datos de contención | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40e28eb246b2c4611a15dc4ce2cf6b1b02dd0100
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263186"
---
# <a name="call-tree-view---contention-data"></a>Vista Árbol de llamadas: datos de contención
La vista Árbol de llamadas muestra las rutas de acceso de ejecución de funciones que se recorrieron en la aplicación de la que se generaron perfiles. La raíz del árbol es el punto de entrada a la aplicación o el componente. Cada nodo de función enumera todas las funciones a las que llamó, el número de veces que se bloqueó la función y la cantidad de tiempo que se bloqueó la función porque estaba luchando por un recurso con otros subprocesos o procesos.  
  
 Los valores en la vista Árbol de llamadas se refieren a las instancias de la función a las que llamó la función primaria en el árbol de llamadas. Los valores de porcentaje se calculan comparando el valor de instancia de función con el número total de contenciones de la ejecución de asignación de perfiles.  
  
## <a name="highlight-the-execution-hot-path"></a>Resaltado de la ruta de acceso activa de ejecución  
 La vista Árbol de llamadas se puede expandir y resaltar la ruta de acceso de ejecución del proceso o la función que creó la mayoría de las contenciones.  
  
-   Para mostrar la ruta de acceso más activa, haga clic con el botón derecho en el proceso o función y, a continuación, haga clic en **Expandir ruta de acceso activa**.  
  
## <a name="set-the-call-tree-root-node"></a>Establecimiento del nodo raíz del árbol de llamadas  
 Cada uno de los procesos de la generación de perfiles se muestra como nodo raíz. Para establecer el nodo inicial de la vista Árbol de llamadas, haga clic con el botón derecho en el nodo que desea establecer como nodo de inicio y, a continuación, haga clic en **Establecer raíz**.  
  
 Al establecer el nodo raíz, se eliminan todas las demás entradas de la vista, excepto el subárbol del nodo seleccionado. Para restablecer el nodo raíz en el nodo original, haga clic con el botón derecho en la vista Árbol de llamadas y, a continuación, haga clic en **Restablecer raíz**.  
  
|Columna|Description|  
|------------|-----------------|  
|**Tiempo de bloqueo exclusivo**|El tiempo que no se pudieron ejecutar en la generación de perfiles las instancias de esta función en esta ruta de acceso de ejecución. El valor no incluye el tiempo de bloqueo de las funciones secundarias a las que llamó la función.|  
|**Porcentaje de tiempo de bloqueo exclusivo**|El porcentaje de tiempo de bloqueo exclusivo de esta función en esta ruta de acceso de ejecución con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Contenciones exclusivas**|El número de contenciones que se produjeron en instancias de esta función en esta ruta de acceso de ejecución. El número no incluye las contenciones de las funciones secundarias a las que llamó la función.|  
|**Porcentaje de contenciones exclusivas**|El porcentaje de contenciones exclusivas de las instancias de esta función llamadas por la función primaria del árbol de llamadas con respecto a todas las contenciones de la ejecución de generación de perfiles.|  
|**Dirección de la función**|Dirección de la función.|  
|**Nombre de la función**|El nombre completo de la función.|  
|**Tiempo de bloqueo inclusivo**|El tiempo total que no se pudieron ejecutar en la generación de perfiles las instancias de esta función en esta ruta de acceso de ejecución. El valor incluye el tiempo de bloqueo de las funciones secundarias a las que llamó la función.|  
|**Porcentaje de tiempo de bloqueo inclusivo**|El porcentaje de tiempo de bloqueo inclusivo de las instancias de esta función en esta ruta de acceso de ejecución con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Contenciones inclusivas**|El número total de contenciones que bloquearon las instancias de esta función en esta ruta de acceso de ejecución. El número incluye las contenciones de las funciones secundarias a las que llamó la función.|  
|**Porcentaje de contenciones inclusivas**|El porcentaje de las contenciones inclusivas de las instancias de esta función en esta ruta de acceso de ejecución con respecto a todas las contenciones de la ejecución de generación de perfiles.|  
|**Nivel**|Nivel de la función en el árbol de llamadas. Solo en informes de línea de comandos de VSReport. Para obtener más información, consulte [VSPerfReport](../profiling/vsperfreport.md).|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view.md)   
 [Vista Árbol de llamadas: instrumentación](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Vista Árbol de llamadas: muestreo](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view-instrumentation-data.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view-sampling-data.md)