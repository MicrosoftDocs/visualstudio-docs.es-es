---
title: 'Vista Líneas: datos de muestreo de memoria de .NET | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e47ed928d32e3cc7ec1ba9a72cf7992ebd4b892
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776985"
---
# <a name="lines-view---net-memory-sampling-data"></a>Vista Líneas: datos de muestreo de memoria de .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista Líneas para los datos de generación de perfiles de asignación de memoria .NET que usa el método de muestreo enumera las instrucciones que asignaron memoria durante la ejecución de la generación de perfiles. Las columnas también incluyen el número de asignaciones y su tamaño.  
  
 En un archivo de origen, una instrucción puede abarcar más de una línea y una sola línea puede incluir más de una instrucción.  
  
 Una instrucción se identifica mediante lo siguiente:  
  
- El archivo de código fuente que contiene la instrucción de la función.  
  
- La función que contiene la instrucción.  
  
- La línea de origen donde se inicia la instrucción.  
  
- El carácter en la línea de origen donde se inicia la instrucción.  
  
- La línea de origen donde finaliza la instrucción.  
  
- El carácter en la línea de origen donde finaliza la instrucción.  
  
  La columna Nombre de línea proporciona una concatenación ordenable de datos del identificador.  
  
  Por definición, una instrucción no llama a otras funciones. Por lo tanto, se muestran solo los valores exclusivos.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Nombre del módulo**|Nombre del módulo que contiene la instrucción.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la instrucción.|  
|**Archivo de código fuente**|El archivo de origen que contiene el nombre de la instrucción.|  
|**Nombre de la función**|El nombre de la función que contiene la instrucción.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de la función**|La dirección de inicio de la función.|  
|**Línea de inicio del origen**|Número de línea inicial en el archivo de origen donde se realizó la asignación.|  
|**Línea de finalización del origen**|Número de línea final en el archivo de origen donde se realizó la asignación.|  
|**Carácter de inicio en el código fuente**|Desplazamiento del carácter de inicio en la línea del archivo de origen donde se realizó la asignación.|  
|**Carácter de finalización en el código fuente**|Desplazamiento del carácter final en la línea del archivo de origen donde se realizó la asignación.|  
|**Nombre de línea**|Un identificador generado por el generador de perfiles de la línea con la siguiente sintaxis:`Source File`**;[**`Line Number Start`**,**`Character Start`**]->;[**`Line Number Start,Character Start`**]**|  
|**Asignaciones exclusivas**|El número total de objetos creados en esta línea.|  
|**Porcentaje de asignaciones exclusivas**|El porcentaje de todos los objetos que se crearon durante la generación de perfiles que se asignaron en esta línea.|  
|**Bytes exclusivos**|El porcentaje de todos los bytes de memoria que se asignaron durante la generación de perfiles que se asignaron en esta línea.|  
|**Porcentaje de bytes exclusivos**|El porcentaje de todos los bytes de memoria que se asignaron durante la generación de perfiles que se asignaron en esta línea.|  
  
## <a name="see-also"></a>Vea también  
 [Vista Líneas](../profiling/lines-view-sampling-data.md)



