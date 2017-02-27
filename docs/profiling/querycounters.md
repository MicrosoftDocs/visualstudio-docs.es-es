---
title: "QueryCounters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# QueryCounters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **QueryCounters** enumera los contadores de rendimiento de la CPU \(hardware\) que están disponibles en el equipo.  
  
 **QueryCounters** debe ser la única opción en la línea de comandos.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### Parámetros  
 None  
  
## Comentarios  
 Si usa el método de instrumentación, el generador de perfiles puede recopilar los valores de uno o varios contadores de rendimiento de la CPU en cada evento de recolección de datos.  Si usa el método de generación de perfiles mediante muestreo, puede especificar un evento de contador y el número de apariciones de evento que se va a utilizar como intervalo de muestreo.  
  
 Diferentes procesadores exponen diferentes contadores de rendimiento de CPU.  El generador de perfiles define un conjunto de contadores genéricos que se pueden utilizar en casi todos procesadores.  La opción **QueryCounters** muestra los nombres de los contadores genéricos y los nombres de los contadores específicos del procesador.  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)