---
title: 'Vista Punteros de instrucción (IP): datos de muestreo de memoria de .NET | Microsoft Docs'
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
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21141483d462df0faee099c22e2b79fc1718880d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566221"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Vista Punteros de instrucción (IP): datos de muestreo de memoria de .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [vista punteros de instrucción (IP): datos de muestreo de memoria de .NET](https://docs.microsoft.com/visualstudio/profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data).  
  
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



