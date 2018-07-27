---
title: 'Vista Punteros de instrucción (IP): datos de muestreo de memoria de .NET | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3b3d0d0334ed8073a125d8b2c435f8e5d58299d4
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844877"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Vista Punteros de instrucción (IP): datos de muestreo de memoria de .NET
La vista Punteros de instrucción para los datos de generación de perfiles de asignación de memoria .NET que se han recopilado mediante el método de muestreo enumera las instrucciones de ensamblado que han asignado memoria durante la generación de perfiles. Las columnas de la vista también incluyen el número de asignaciones y su tamaño.  
  
 Solo se muestran los valores exclusivos.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Nombre del módulo**|El nombre del módulo que contiene la instrucción.|  
|**Ruta de acceso del módulo**|La ruta de acceso del módulo que contiene la instrucción.|  
|**Archivo de código fuente**|El archivo de origen que contiene el nombre de la instrucción.|  
|**Nombre de la función**|Nombre de la función.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de la función**|La dirección de inicio de la función.|  
|**Línea de inicio del origen**|Número de línea inicial en el archivo de origen donde se realizó la asignación.|  
|**Línea de finalización del origen**|Número de línea final en el archivo de origen donde se realizó la asignación.|  
|**Carácter de inicio en el código fuente**|Desplazamiento del carácter de inicio en la línea del archivo de origen donde se realizó la asignación.|  
|**Carácter de finalización en el código fuente**|Desplazamiento del carácter final en la línea del archivo de origen donde se realizó la asignación.|  
|**Dirección de instrucción**|Dirección de la instrucción.|  
|**Asignaciones exclusivas**|Número total de objetos que ha creado la instrucción.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que ha asignado la instrucción.|  
|**Bytes exclusivos**|Número de bytes de memoria asignados durante la generación de perfiles que ha asignado la instrucción.|  
|**Porcentaje de bytes exclusivos**|Porcentaje de todos los bytes de memoria asignados durante la generación de perfiles que ha asignado la instrucción.|  
  
## <a name="see-also"></a>Vea también  
 [Vista Punteros de instrucción (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)