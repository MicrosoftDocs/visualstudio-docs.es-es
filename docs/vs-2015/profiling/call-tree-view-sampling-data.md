---
title: 'Vista Árbol de llamadas: datos de muestreo | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7f7f4f435b0b00fb68395d0c00670d7f89c9cb2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578183"
---
# <a name="call-tree-view---sampling-data"></a>Vista Árbol de llamadas: datos de muestreo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [vista de árbol de llamadas: datos de muestreo](https://docs.microsoft.com/visualstudio/profiling/call-tree-view-sampling-data).  
  
La vista Árbol de llamadas muestra las rutas de acceso de ejecución de funciones que se recorrieron en la aplicación de la que se generaron perfiles.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 La raíz del árbol es el punto de entrada a la aplicación o el componente. Cada nodo de función muestra todas las funciones a las que llamó, así como los datos de rendimiento de esas llamadas a funciones.  
  
 Los valores en la vista Árbol de llamadas se refieren a las instancias de la función a las que llamó la función primaria en el árbol de llamadas. Los valores de porcentaje se calculan comparando el valor de la instancia de la función con el número total de muestras en la ejecución de generación de perfiles.  
  
## <a name="highlighting-the-execution-hot-path"></a>Resaltar la ruta de acceso activa de ejecución  
 La vista Árbol de llamadas también puede expandir y resaltar la ruta de acceso de ejecución del proceso o la función de que se han tomado muestras con más frecuencia. Para mostrar la ruta de acceso más activa, haga clic con el botón derecho en el proceso o la función y, después, haga clic en **Expandir ruta de acceso activa**.  
  
## <a name="setting-the-call-tree-root-node"></a>Establecer el nodo raíz del árbol de llamadas  
 Cada proceso en la ejecución de generación de perfiles se muestra como un nodo raíz. Para establecer el nodo de inicio de la vista Árbol de llamadas, haga clic con el botón derecho en el nodo que quiere establecer como nodo de inicio y seleccione **Establecer raíz**.  
  
 Al establecer el nodo raíz, se eliminan todas las demás entradas de la vista, excepto el subárbol del nodo seleccionado. Para restablecer el nodo raíz en el nodo original, haga clic con el botón derecho en la ventana de la vista Árbol de llamadas y seleccione **Restablecer raíz**.  
  
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
|**Nivel**|La profundidad de esta función en el árbol de llamadas. Solo disponible en los informes de línea de comandos de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Muestras exclusivas**|El número de muestras que se recopilaron en esta función cuando la llamó la función primaria en el árbol de llamadas. Este número no incluye aquellas muestras recopiladas en funciones a las que llamó la función.|  
|**Porcentaje de muestras exclusivas**|El porcentaje de todas las muestras de la ejecución de generación de perfiles que eran muestras exclusivas de esta función cuando la llamó la función primaria en el árbol de llamadas.|  
|**Muestras inclusivas**|El número de muestras que se recopilaron en esta función cuando la llamó la función primaria en el árbol de llamadas. Este número incluye aquellas muestras recopiladas en funciones a las que llamó la función.|  
|**Porcentaje de muestras inclusivas**|El porcentaje de todas las muestras de la ejecución de generación de perfiles que eran muestras inclusivas de esta función cuando la llamó la función primaria en el árbol de llamadas.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Árbol de llamadas: datos de muestreo del generador de perfiles](../profiling/call-tree-view-sampling-data.md)   
 [Vista Árbol de llamadas: muestreo](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Vista Árbol de llamadas: instrumentación](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Vista Árbol de llamadas](../profiling/call-tree-view-instrumentation-data.md)



