---
title: "Vista Punteros de instrucción (IP): datos de muestreo de memoria de .NET | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c37cc7b63a8f93c3b63cdda0bb9ce460a01d195a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Vista Punteros de instrucción (IP): datos de muestreo de memoria de .NET
La vista Punteros de instrucción para los datos de generación de perfiles de asignación de memoria .NET que se han recopilado mediante el método de muestreo enumera las instrucciones de ensamblado que han asignado memoria durante la generación de perfiles. Las columnas de la vista también incluyen el número de asignaciones y su tamaño.  
  
 Solo se muestran los valores exclusivos.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre del módulo**|El nombre del módulo que contiene la instrucción.|  
|**Ruta de acceso del módulo**|La ruta de acceso del módulo que contiene la instrucción.|  
|**Archivo de origen**|El archivo de origen que contiene el nombre de la instrucción.|  
|**Nombre de la función**|Nombre de la función.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de función**|La dirección de inicio de la función.|  
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
 [Vista Punteros de instrucciones (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)