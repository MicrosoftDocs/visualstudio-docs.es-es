---
title: "Vista Punteros de instrucción (IP): Datos de muestreo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 86a1e2fd1f25926eb8e6864d7b5174b192c4f5c9
ms.lasthandoff: 02/22/2017

---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Vista Punteros de instrucción (IP): Datos de muestreo
La vista Punteros de instrucción de datos de muestreo muestra los datos de rendimiento de las instrucciones de ensamblado que se estaban ejecutando directamente cuando se recopilaron las muestras en la ejecución de generación de perfiles.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Identificador del proceso**|Identificador de proceso (PID) de la ejecución de generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre del módulo**|El nombre del módulo que contiene la instrucción.|  
|**Ruta de acceso del módulo**|La ruta de acceso del módulo que contiene la instrucción.|  
|**Archivo de origen**|El archivo de origen que contiene el nombre de la instrucción.|  
|**Nombre de la función**|El nombre de la función que contiene la instrucción.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de función**|La dirección de memoria inicial de la función en el binario cargado.|  
|**Línea de inicio del origen**|Número de línea inicial en el archivo de origen donde se recopiló esta muestra.|  
|**Línea de finalización del origen**|Número de la línea de finalización del archivo de origen donde se recopiló esta muestra.|  
|**Carácter de inicio en el código fuente**|Desplazamiento del carácter de inicio en la línea del archivo de origen donde se recopiló esta muestra.|  
|**Carácter de finalización en el código fuente**|Desplazamiento del carácter final en la línea del archivo de origen donde se recopiló esta muestra.|  
|**Dirección de instrucción**|La dirección de la instrucción en el binario cargado.|  
|**Muestras exclusivas**|El número total de muestras recopiladas cuando la instrucción se estaba ejecutando.|  
|**Porcentaje de muestras exclusivas**|El porcentaje de todas las muestras que se recopilaron durante la generación de perfiles mientras se ejecutaba la instrucción.|  
  
## <a name="see-also"></a>Vea también  
 [Vista Punteros de instrucción (IP): Muestreo](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
