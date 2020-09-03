---
title: 'Vista Funciones: datos de contención | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1aaab824f40c0cd6ba0a240a6f3035d7ebcccd00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141899"
---
# <a name="functions-view---contention-data"></a>Vista Funciones: datos de contención
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista de informe Funciones de datos de contención enumera las funciones en la ejecución de generación de perfiles a las que se les ha impedido la ejecución durante la ejecución de generación de perfiles.  
  
 En la tabla siguiente, se explican los valores que se muestran en la vista Funciones de un archivo de datos de generación de perfiles recopilado con el método de simultaneidad.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo de bloqueo exclusivo**|Tiempo durante el cual esta función no pudo ejecutar código en el cuerpo de la función. No se incluye el tiempo de bloqueo de las funciones a las que llamó la función.|  
|**Porcentaje de tiempo de bloqueo exclusivo**|Porcentaje de tiempo de bloqueo exclusivo de esta función con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Contenciones exclusivas**|Número de veces en las que esta función no pudo ejecutar código en el cuerpo de la función. No se incluyen las contenciones en las funciones a las que ha llamado la función.|  
|**Porcentaje de contenciones exclusivas**|Porcentaje de contenciones exclusivas de esta función con respecto a todas las contenciones en la ejecución de generación de perfiles.|  
|**Dirección de la función**|Dirección de la función.|  
|**Nombre de la función**|El nombre completo de la función.|  
|**Tiempo de bloqueo inclusivo**|Tiempo durante el cual esta función o una función llamada por esta función no pudieron ejecutarse.|  
|**Porcentaje de tiempo de bloqueo inclusivo**|Porcentaje de tiempo de bloqueo inclusivo de esta función o módulo con respecto al tiempo de bloqueo total de la ejecución de generación de perfiles.|  
|**Contenciones inclusivas**|Número de veces que esta función o una función llamada por esta función no pudieron ejecutarse.|  
|**Porcentaje de contenciones inclusivas**|Porcentaje de contenciones inclusivas de esta función o módulo con respecto a todas las contenciones en la ejecución de generación de perfiles.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Identificador del proceso**|El Id. del proceso (PID) en el que se estaba ejecutando la función.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Archivo de código fuente**|Archivo de origen que contiene la definición de esta función.|  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista funciones](../profiling/functions-view.md)   
 [Vista funciones: instrumentación](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Vista funciones: muestreo](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Vista funciones](../profiling/functions-view-instrumentation-data.md)   
 [Vista Funciones](../profiling/functions-view-sampling-data.md)
