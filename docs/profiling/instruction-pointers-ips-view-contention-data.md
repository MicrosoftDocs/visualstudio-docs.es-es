---
title: "Vista Punteros de instrucci&#243;n (IP): Datos de contenci&#243;n de generador de perfiles | Microsoft Docs"
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
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Punteros de instrucci&#243;n (IP): Datos de contenci&#243;n de generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista IP de datos de contención muestra los datos de las instrucciones de ensamblado cuya ejecución se bloqueó en la ejecución de generación de perfiles.  
  
 En la tabla siguiente se explican los valores de las columnas de la vista Punteros de instrucción.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Tiempo de bloqueo exclusivo**|Tiempo bloqueado en esta función.|  
|**% de tiempo de bloqueo exclusivo**|Porcentaje de tiempo bloqueado mientras se ejecutó la instrucción.|  
|**Contenciones exclusivas**|El número de contenciones que se produjeron mientras se ejecutó la instrucción.|  
|**% de contenciones exclusivas**|El porcentaje de todas las contenciones de la ejecución de generación de perfiles que se produjeron mientras se ejecutó la instrucción.|  
|**Dirección de función**|Dirección de memoria de inicio de la función en el binario cargado.|  
|**Nombre de la función**|Nombre de la función que contiene la instrucción.|  
|**Dirección de instrucción**|Dirección de memoria de la instrucción en el binario cargado.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Nombre de módulo**|Nombre del módulo que contiene la instrucción.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la instrucción.|  
|**Id. de proceso**|Identificador de proceso \(PID\) del proceso para el que se realizó la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Comienzo del carácter de código fuente**|El desplazamiento del carácter en la línea del archivo de origen en la que se inicia esta instrucción.|  
|**Fin del carácter de código fuente**|El desplazamiento del carácter en la línea del archivo de origen en la que finaliza esta instrucción.|  
|**Archivo de origen**|Archivo de origen que contiene la instrucción.|  
|**Comienzo de la línea de código fuente**|El número de línea en el archivo de origen en el que se inicia esta instrucción.|  
|**Fin de la línea de código fuente**|El número de línea en el archivo de origen en el que finaliza esta instrucción.|  
  
## Vea también  
 [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md)   
 [Vista Punteros de instrucciones \(IP\)](../profiling/instruction-pointers-ips-view.md)   
 [Vista Punteros de instrucciones \(IP\) \- Muestreo](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [Vista Punteros de instrucciones \(IP\)](../profiling/instruction-pointers-ips-view-sampling-data.md)