---
title: 'Vista Punteros de instrucción (IP): Datos de muestreo | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2fdc7069ee0d422fd59b297b4b99a982d265e3a2
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844285"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Vista Punteros de instrucción (IP): Datos de muestreo
La vista Punteros de instrucción de datos de muestreo muestra los datos de rendimiento de las instrucciones de ensamblado que se estaban ejecutando directamente cuando se recopilaron las muestras en la ejecución de generación de perfiles.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre de proceso**|Nombre del proceso.|  
|**Nombre del módulo**|El nombre del módulo que contiene la instrucción.|  
|**Ruta de acceso del módulo**|La ruta de acceso del módulo que contiene la instrucción.|  
|**Archivo de código fuente**|El archivo de origen que contiene el nombre de la instrucción.|  
|**Nombre de la función**|El nombre de la función que contiene la instrucción.|  
|**Número de línea de la función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de función**|La dirección de memoria inicial de la función en el binario cargado.|  
|**Línea de inicio del origen**|Número de línea inicial en el archivo de origen donde se recopiló esta muestra.|  
|**Línea de finalización del origen**|Número de la línea de finalización del archivo de origen donde se recopiló esta muestra.|  
|**Carácter de inicio en el código fuente**|Desplazamiento del carácter de inicio en la línea del archivo de origen donde se recopiló esta muestra.|  
|**Carácter de finalización en el código fuente**|Desplazamiento del carácter final en la línea del archivo de origen donde se recopiló esta muestra.|  
|**Dirección de instrucción**|La dirección de la instrucción en el binario cargado.|  
|**Muestras exclusivas**|El número total de muestras recopiladas cuando la instrucción se estaba ejecutando.|  
|**Porcentaje de muestras exclusivas**|El porcentaje de todas las muestras que se recopilaron durante la generación de perfiles mientras se ejecutaba la instrucción.|  
  
## <a name="see-also"></a>Vea también  
 [Vista Punteros de instrucción (IP): muestreo](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)