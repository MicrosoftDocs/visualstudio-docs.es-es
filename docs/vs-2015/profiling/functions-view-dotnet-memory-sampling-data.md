---
title: 'Vista Funciones: datos de muestreo de memoria de .NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e77c6c2b3bf079e8aae88c9779c3b487ff97fe7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68141873"
---
# <a name="functions-view---net-memory-sampling-data"></a>Vista Funciones: datos de muestreo de memoria de .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista Funciones de los datos de generación de perfiles de asignación de memoria de .NET recopilados mediante el método de muestreo enumera las funciones que han asignado memoria durante la ejecución de generación de perfiles e informa del tamaño y número de asignaciones.  
  
|Columna|DESCRIPCIÓN|  
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
  
## <a name="see-also"></a>Otras referencias  
 [Vista Funciones: instrumentación](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Vista Funciones](../profiling/functions-view-sampling-data.md)   
 [Vista Funciones](../profiling/functions-view-instrumentation-data.md)
