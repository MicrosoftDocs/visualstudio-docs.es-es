---
title: "Args | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Args
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **Args** de VSPerfCmd.exe especifica una lista de argumentos que se pasan a la aplicación de destino del subcomando **Launch**.  
  
 **Args** sólo se puede usar cuando también se especifica **Launch** en la línea de comandos.  **Args** es opcional si no se especifica **Launch**.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### Parámetros  
 `Arguments`  
 Una lista de argumentos para la aplicación de destino del comando **Launch**.  
  
## Opciones necesarias  
 **Launch:** `AppName`  
 Inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.  
  
## Ejemplo  
 En el ejemplo siguiente se utiliza la opción **Args** para pasar argumentos a TestApp.exe.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)