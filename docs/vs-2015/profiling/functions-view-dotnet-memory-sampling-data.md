---
title: 'Vista Funciones: datos de muestreo de memoria de .NET | Microsoft Docs'
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
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ac8c19c02754d17a8af3b5472ecd580948793962
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580143"
---
# <a name="functions-view---net-memory-sampling-data"></a>Vista Funciones: datos de muestreo de memoria de .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [vista funciones: datos de muestreo de memoria de .NET](https://docs.microsoft.com/visualstudio/profiling/functions-view-dotnet-memory-sampling-data).  
  
La vista Funciones de los datos de generación de perfiles de asignación de memoria de .NET recopilados mediante el método de muestreo enumera las funciones que han asignado memoria durante la ejecución de generación de perfiles e informa del tamaño y número de asignaciones.  
  
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
|**Asignaciones inclusivas**|Número total de objetos asignados en esta función y sus funciones secundarias.|  
|**Porcentaje de asignaciones inclusivas**|Porcentaje de todos los objetos que se asignaron durante la ejecución de la generación de perfiles que eran asignaciones inclusivas de esta función.|  
|**Asignaciones exclusivas**|Número de objetos creados cuando la función se estaba ejecutando directamente en la parte superior de la pila de llamadas. Este número no incluye los objetos creados en funciones secundarias.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de todos los objetos que se han asignado durante la ejecución de la generación de perfiles que eran asignaciones exclusivas de esta función.|  
|**Porcentaje de bytes inclusivos**|Número de bytes de memoria asignados por esta función y sus funciones secundarias.|  
|**Porcentaje de bytes inclusivos**|Porcentaje de todos los bytes de memoria que se asignaron durante la ejecución de la generación de perfiles que eran bytes inclusivos de esta función.|  
|**Bytes exclusivos**|Número de bytes de memoria asignados por esta función, pero no por sus funciones secundarias.|  
|**Porcentaje de bytes exclusivos**|Porcentaje de todos los bytes de memoria que se asignaron durante la ejecución de la generación de perfiles que eran bytes exclusivos de esta función.|  
  
## <a name="see-also"></a>Vea también  
 [Vista Funciones: instrumentación](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Vista Funciones](../profiling/functions-view-sampling-data.md)   
 [Vista Funciones](../profiling/functions-view-instrumentation-data.md)



