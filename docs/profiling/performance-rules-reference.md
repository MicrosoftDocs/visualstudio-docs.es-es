---
title: Referencia de reglas de rendimiento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3d947dbc3fae436fa64d3effa963df5445991be
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831292"
---
# <a name="performance-rules-reference"></a>Referencia de reglas de rendimiento
Las reglas de rendimiento de las herramientas de generación de perfiles proporcionan advertencias adicionales e información sobre el rendimiento de la aplicación. Las reglas de rendimiento analizan los datos en un proceso de generación de perfiles recopilados de orígenes como los contadores de rendimiento de procesador y de Windows. Los mensajes de regla aparecen en la ventana Salida de error del entorno de desarrollo integrado de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Los mensajes se muestran con uno de los siguientes niveles de regla:  
  
|||  
|-|-|  
|**Error**|Pocas reglas generan mensajes de error, dado que la mayoría de los problemas de rendimiento no son errores propiamente dichos. Un mensaje de error puede indicar que no es posible recopilar datos de generación de perfiles.|  
|**Advertencia**|Las advertencias indican un área de la aplicación que puede ser una fuente de problemas de rendimiento o que podría beneficiarse de las optimizaciones.|  
|**Información**|Los mensajes de información indican que el análisis de una condición de regla no alcanzó el umbral para generar un mensaje de error o que la información en el mensaje es útil, pero no refleja un problema de rendimiento.|  
  
## <a name="in-this-section"></a>En esta sección  
 [Reglas de rendimiento por identificador](../profiling/performance-rules-by-id.md)  
  
 Las reglas de rendimiento de las herramientas de generación de perfiles se organizan en cuatro categorías:  
  
|||  
|-|-|  
|[Reglas de rendimiento de uso de .NET Framework](../profiling/dotnet-framework-usage-performance-rules.md)|Reglas que le ayudarán a utilizar .NET Framework de forma más eficaz.|  
|[Reglas de rendimiento de memoria y paginación](../profiling/memory-and-paging-performance-rules.md)|Reglas que analizan el comportamiento de paginación y la memoria administrada de la aplicación.|  
|[Reglas de uso de herramientas de generación de perfiles](../profiling/profiling-tools-usage-rules.md)|Reglas que le ayudarán a utilizan las herramientas de generación de perfiles de forma más eficaz.|  
|[Reglas de rendimiento de la supervisión de recursos](../profiling/resource-monitoring-performance-rules.md)|Mensajes de información sobre el uso del procesador y la memoria en un proceso de generación de perfiles.|