---
title: "Vista de punteros de instrucci&#243;n (IPs): datos de muestreo de memoria de .NET del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Punteros de instrucciones (vista)"
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista de punteros de instrucci&#243;n (IPs): datos de muestreo de memoria de .NET del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista IP de datos de generación de perfiles de asignación de memoria .NET recopilados mediante el método de muestreo muestra las instrucciones de ensamblado que asignaron memoria durante la ejecución de generación de perfiles.  Las columnas de la vista también enumeran el tamaño y número de asignaciones.  
  
 Solamente se enumeran los valores exclusivos.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre de módulo**|Nombre del módulo que contiene la instrucción.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la instrucción.|  
|**Archivo de origen**|Archivo de origen que contiene la instrucción.|  
|**Nombre de la función**|Nombre de la función.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de función**|Dirección inicial de la función.|  
|**Comienzo de la línea de código fuente**|Número de línea inicial en el archivo de origen donde se produjo la asignación.|  
|**Fin de la línea de código fuente**|Número de línea final en el archivo de origen donde se produjo la asignación.|  
|**Comienzo del carácter de código fuente**|Desplazamiento del carácter inicial en la línea del archivo de origen donde se produjo la asignación.|  
|**Fin del carácter de código fuente**|Desplazamiento del carácter final en la línea del archivo de origen donde se produjo la asignación.|  
|**Dirección de instrucción**|Dirección de la instrucción.|  
|**Asignaciones de exclusión**|Número total de objetos creados por la instrucción.|  
|**Porcentaje de asignaciones exclusivas**|Porcentaje de todos los objetos creados durante la generación de perfiles que fueron asignados por la instrucción.|  
|**Bytes exclusivos**|Número de bytes de memoria asignados en la ejecución de generación de perfiles que fueron asignados por la instrucción.|  
|**Porcentaje de bytes exclusivos**|Porcentaje de bytes asignados por la instrucción con respecto a todos los bytes de memoria asignados durante la ejecución de generación de perfiles.|  
  
## Vea también  
 [Vista Punteros de instrucciones \(IP\)](../profiling/instruction-pointers-ips-view-sampling-data.md)