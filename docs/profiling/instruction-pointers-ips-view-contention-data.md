---
title: 'Vista Punteros de instrucción (IP): Datos de contención | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41d5a490ddd4b426a3c03f9e5bbea94d18660200
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946339"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Vista Punteros de instrucción (IP): Datos de contención
La vista Punteros de instrucción de datos de contención muestra los datos de las instrucciones de ensamblado cuya ejecución se bloqueó durante la generación de perfiles.  
  
 En la siguiente tabla se explican los valores de las columnas de la vista Punteros de instrucción.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Tiempo de bloqueo exclusivo**|El tiempo de bloqueo en esta función.|  
|**Porcentaje de tiempo de bloqueo exclusivo**|El porcentaje de tiempo de bloqueo mientras se ejecutaba la instrucción.|  
|**Contenciones exclusivas**|El número de contenciones que se produjeron mientras se ejecutaba la instrucción.|  
|**Porcentaje de contenciones exclusivas**|El porcentaje de todas las contenciones que se produjeron durante la generación de perfiles mientras se ejecutaba la instrucción.|  
|**Dirección de la función**|La dirección de memoria inicial de la función en el binario cargado.|  
|**Nombre de la función**|El nombre de la función que contiene la instrucción.|  
|**Dirección de instrucción**|La dirección de memoria de la instrucción en el binario cargado.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Nombre del módulo**|El nombre del módulo que contiene la instrucción.|  
|**Ruta de acceso del módulo**|La ruta de acceso del módulo que contiene la instrucción.|  
|**Identificador del proceso**|El identificador de proceso (PID) del proceso del que se generaron perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Carácter de inicio en el código fuente**|El desplazamiento del carácter en la línea del archivo de origen donde empieza esta instrucción.|  
|**Carácter de finalización en el código fuente**|El desplazamiento del carácter en la línea del archivo de origen donde acaba esta instrucción.|  
|**Archivo de origen**|El archivo de origen que contiene el nombre de la instrucción.|  
|**Línea de inicio del origen**|El número de línea en el archivo de origen en el que comienza esta instrucción.|  
|**Línea de finalización del origen**|El número de línea en el archivo de origen en el que finaliza esta instrucción.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Punteros de instrucción (IP)](../profiling/instruction-pointers-ips-view.md)   
 [Vista Punteros de instrucción (IP): muestreo](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [Vista Punteros de instrucción (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)