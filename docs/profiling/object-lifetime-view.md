---
title: Visa Duración del objeto| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 247c81d46ee8f5ae916a2a024620e4f4eb864194
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255624"
---
# <a name="object-lifetime-view"></a>Vista Duración del objeto
La vista Duración del objeto está disponible cuando se activa **Also collect .NET object lifetime data** (Recopilar también datos de duración del objeto de .NET) en las páginas de propiedades de la **sesión de rendimiento**.  
  
 El recolector de elementos no utilizados de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] administra la asignación y liberación de la memoria para la aplicación. Para optimizar el rendimiento del recolector de elementos no utilizados, el montón administrado se divide en tres generaciones: 0, 1 y 2. El recolector de elementos no utilizados del runtime almacena los nuevos objetos en la generación 0. Los objetos que sobreviven a las recopilaciones se promueven y almacenan en las generaciones 1 y 2.  
  
 El recolector de elementos no utilizados recupera memoria desasignando una generación completa de objetos. Para los objetos creados por la aplicación de la que se generaron perfiles, la vista Duración del objeto muestra el número y tamaño de los objetos y la generación en la que se recuperan.  
  
## <a name="general"></a>General  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Nombre de la clase**|Nombre de clase del tipo asignado.|  
|**Identificador del proceso**|El identificador del proceso de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Nombre del módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
  
## <a name="instance-data"></a>Datos de instancia  
 Datos de instancia indica el número de objetos del tipo que se crearon en la generación de perfiles y la generación en la que se desasignaron objetos por parte del recolector de elementos no utilizados.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Instancias**|Número de asignaciones de objetos de este tipo.|  
|**Total de instancias %**|Porcentaje del número total de asignaciones que se realizaron en la generación de perfiles.|  
|**Instancias recopiladas en la generación 0**|Número de instancias del tipo que se han desasignado en la generación 0 del algoritmo de recolección de elementos no utilizados.|  
|**Instancias recopiladas en la generación 1**|Número de instancias del tipo que se han desasignado en la generación 1 del algoritmo de recolección de elementos no utilizados.|  
|**Instancias recopiladas en la generación 2**|Número de instancias del tipo que se han desasignado en la generación 2 del algoritmo de recolección de elementos no utilizados.|  
|**Instancias activas al final**|Número de instancias del tipo que no se han desasignado hasta el final de la generación de perfiles.|  
  
## <a name="size-byte-data"></a>Tamaño (bytes) de datos  
 El tamaño (bytes) de datos indica el número de objetos del tipo que se crearon en la generación de perfiles y la cantidad de memoria que se reclamó en cada generación en la que se desasignaron los objetos.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Total de bytes asignados**|Número total de bytes de todas las instancias del tipo.|  
|**Total de bytes %**|Porcentaje del número total de bytes asignados en la generación de perfiles, que se asignaron para instancias de este tipo.|  
|**Bytes recopilados en la generación 0**|Tamaño de las instancias del tipo que se han desasignado en la generación 0 del algoritmo de recolección de elementos no utilizados.|  
|**Bytes recopilados en la generación 1**|Tamaño de las instancias del tipo que se han desasignado en la generación 1 del algoritmo de recolección de elementos no utilizados.|  
|**Bytes recopilados en la generación 2**|Tamaño de las instancias del tipo que se han desasignado en la generación 2 del algoritmo de recolección de elementos no utilizados.|  
  
## <a name="large-object-heap-data"></a>Tamaño de montón de objetos grandes  
 El asignador de memoria de .NET administra objetos muy grandes en una ubicación que es independiente del montón administrado estándar. Los datos de montón de objeto grande indican el número y el tamaño de los objetos del tipo que se administraron en esta ubicación.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Instancias de montón de objeto grande recopiladas**|Número de instancias de este tipo que se encontraban en el montón de objeto grande y que se recopilaron en la generación de perfiles.|  
|**Bytes de montón de objeto grande recopilados**|Tamaño, en bytes, de las instancias de este tipo que se encontraban en el montón de objeto grande y que se recopilaron en la generación de perfiles.|  
  
## <a name="see-also"></a>Vea también  
 [Vistas de datos de memoria de .NET](../profiling/dotnet-memory-data-views.md)