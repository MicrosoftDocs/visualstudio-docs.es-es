---
title: "Apagar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Apagar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **Shutdown** espera que el proceso actualmente perfilado se detenga o se desasocie y, a continuación, desactiva el generador de perfiles y cierra el archivo de datos de generación de perfiles.  La opción **Shutdown** debe ser el último comando de una ejecución de generación de perfiles.  
  
 Si no se especifica un parámetro de tiempo de espera, la opción **Shutdown** esperará indefinidamente.  Si se especifica un parámetro de tiempo de espera, la opción vuelve tras el número especificado de segundos sin desactivar el generador de perfiles ni cerrar el archivo de datos.  
  
 La opción **Shutdown** debe ser la única opción especificada en la línea de comandos.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### Parámetros  
 `Timeout`  
 -   \(Opcional\) Si se especifica, la opción vuelve tras el número especificado de segundos sin desactivar el generador de perfiles ni cerrar el archivo de datos de generación de perfiles.  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)