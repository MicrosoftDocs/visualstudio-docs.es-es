---
title: 'Vista Árbol de llamadas: datos de muestreo de memoria de .NET | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6667d0e0ad76210434f40eaf89e4790430ffb0e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758605"
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Vista Árbol de llamadas: datos de muestreo de memoria de .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista Árbol de llamadas muestra las rutas de acceso de ejecución de funciones que se recorrieron en la aplicación de la que se generaron perfiles. La raíz del árbol es el punto de entrada a la aplicación o el componente. Cada nodo de función muestra todas las funciones a las que ha llamado, así como los datos de asignación de memoria de .NET de esas llamadas a funciones.  
  
 Los valores en la vista Árbol de llamadas se refieren a las instancias de la función a las que llamó la función primaria en el árbol de llamadas. Los valores de porcentaje se calculan mediante la comparación del valor de instancia de función con el tamaño o número total de asignaciones de la ejecución de asignación de perfiles.  
  
## <a name="highlighting-the-execution-hot-path"></a>Resaltar la ruta de acceso activa de ejecución  
 La vista Árbol de llamadas puede expandir y resaltar la ruta de acceso de ejecución del proceso o la función que creó la mayoría de los objetos de memoria, o los más grandes. Para mostrar la ruta de acceso más activa, haga clic con el botón derecho en el proceso o función y, a continuación, haga clic en **Expandir ruta de acceso activa**.  
  
## <a name="setting-the-call-tree-root-node"></a>Establecer el nodo raíz del árbol de llamadas  
 Cada proceso en la ejecución de generación de perfiles se muestra como un nodo raíz. Para establecer el nodo de inicio de la vista Árbol de llamadas en otro nodo, haga clic con el botón derecho en el nodo que quiere establecer como nodo de inicio y seleccione **Establecer raíz**.  
  
 Al establecer el nodo raíz, se eliminan todas las demás entradas de la vista, excepto el subárbol del nodo seleccionado. Puede restablecer el nodo raíz en el nodo que estaba viendo; para ello, haga clic con el botón derecho en la ventana de la vista Árbol de llamadas y seleccione **Restablecer raíz**.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre de la función**|El nombre completo de la función.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de la función**|Dirección de la función.|  
|**Nivel**|La profundidad de esta función en el árbol de llamadas.|  
|**Asignaciones inclusivas**|Número de objetos asignados por las instancias de esta función a las que llamó la función primaria del árbol de llamadas. Este número incluye las asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de asignaciones inclusivas**|El porcentaje de todos los objetos que se crearon durante la ejecución de la generación de perfiles que eran asignaciones inclusivas de esta función.|  
|**Asignaciones exclusivas**|Número de objetos asignados por las instancias de esta función a las que llamó la función primaria del árbol de llamadas. Este número no incluye las asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de objetos creados en la ejecución de generación de perfiles que eran asignaciones exclusivas de las instancias de la función llamadas por la función primaria del árbol de llamadas.|  
|**Porcentaje de bytes inclusivos**|Número de bytes en memoria asignados por las instancias de esta función a las que ha llamado la función primaria del árbol de llamadas. Este número incluye las asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de bytes inclusivos**|El porcentaje de todos los bytes de memoria que se asignaron durante la ejecución de la generación de perfiles que eran asignaciones inclusivas de esta función.|  
|**Bytes exclusivos**|Número de bytes en memoria asignados por las instancias de esta función a las que ha llamado la función primaria del árbol de llamadas. Este número no incluye las asignaciones realizadas por funciones secundarias.|  
|**Porcentaje de bytes exclusivos**|El porcentaje de todos los bytes de memoria que se asignaron durante la ejecución de la generación de perfiles que eran asignaciones exclusivas de esta función.|  
  
## <a name="see-also"></a>Vea también  
 [Vista Árbol de llamadas: instrumentación](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view-sampling-data.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view-instrumentation-data.md)



