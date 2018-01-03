---
title: 'Vista Llamador y destinatario: datos de muestreo | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 81c10d85b9dc88115e7dbc57a03a6da4362fa945
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="caller--callee-view---sampling-data"></a>Vista Llamador y destinatario: datos de muestreo
La vista Llamador y destinatario muestra información de generación de perfiles para una función seleccionada y sus funciones primarias y secundarias. La vista Llamador y destinatario contiene tres cuadrículas.  
  
 **Función actual** se muestra en la cuadrícula central e incluye información sobre la generación de perfiles para la función seleccionada. Los valores incluyen todas las llamadas a la función que se muestrearon.  
  
 **Funciones que llamaron a la función actual** se muestra en la cuadrícula superior e incluye las contribuciones individuales de las funciones de llamador (primarias) a los valores de la función seleccionada (actual).  
  
 **Funciones llamadas por la función actual** se muestra en la cuadrícula inferior e incluye información de generación de perfiles para las funciones de destinatario (secundarias) de la función seleccionada cuando la función actual llamó a la función secundaria.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Columna|Description|  
|------------|-----------------|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre de la función**|El nombre completo de la función.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de la función**|Dirección de la función.|  
|**Type**|El contexto de la función:<br /><br /> -   **0**: la función actual<br />-   **1**: una función que llama a la función actual<br />-   **2**: una función llamada por la función actual|  
|**Nombre de la función raíz**|El nombre de la función actual.|  
|**Muestras inclusivas**|-   En la función actual, el número de muestras que se recopilaron aunque se estaba ejecutando esta función o una de sus funciones secundarias.<br />-   En una función de llamador, el número de muestras inclusivas de la función actual que se recopilaron cuando esta función llamó a la función actual.<br />-   En una función de destinatario, el número de muestras inclusivas de esta función que se recopilaron cuando la función actual llamó a esta función.|  
|**Porcentaje de muestras inclusivas**|El porcentaje de todas las muestras de la ejecución de generación de perfiles que fueron muestras inclusivas de esta función.|  
|**Muestras exclusivas**|-   En la función actual, el número de muestras en la ejecución de generación de perfiles que se recopilaron cuando esta función se estaba ejecutando directamente; es decir, cuando esta función estaba en la parte superior de la pila de llamadas. Las muestras que se recopilan cuando se están ejecutando las funciones secundarias de esta función no se cuentan en los recuentos exclusivos.<br />-   En una función de llamador, el número de muestras exclusivas de la función actual que se recopilaron cuando esta función llamó a la función actual.<br />-   En una función de destinatario, el número de muestras exclusivas de esta función que se recopilaron cuando la función actual llamó a esta función.|  
|**Porcentaje de muestras exclusivas**|El porcentaje de todas las muestras de la ejecución de generación de perfiles que fueron muestras exclusivas de esta función.|  
  
## <a name="see-also"></a>Vea también  
 [Vista Llamador y destinatario: datos de muestreo de memoria de .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Vista Llamador y destinatario: datos de instrumentación de memoria de .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Vista Llamador y destinatario: datos de instrumentación](../profiling/caller-callee-view-instrumentation-data.md)