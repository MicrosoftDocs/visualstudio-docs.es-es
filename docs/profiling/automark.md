---
title: "AutoMark | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AutoMark
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **AutoMark** especifica el número de milisegundos entre la recolección de eventos del contador de rendimiento de software de Windows.  Los contadores de rendimiento de Windows se especifican en la opción **WinCounter**.  
  
 Solamente se puede especificar una opción **AutoMark** en la línea de comandos.  Observe que el intervalo de muestreo de **WinCounter** especificado por **AutoMark** es independiente del intervalo del muestreo principal.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### Parámetros  
 `Milliseconds`  
 Especifica el número de milisegundos entre recopilaciones de eventos del contador de rendimiento de Windows.  
  
## Opciones necesarias  
 **WinCounter:** `Path`  
 Especifica el contador de rendimiento de Windows a recolectar.  Cuando esté utilizando el método de instrumentación, puede especificar varios contadores de Windows.  Cuando esté utilizando el método de muestreo, solamente podrá especificar un contador de software.  La opción **WinCounter** se debe especificar en una línea de comandos que contenga la opción **Start**.  
  
## Ejemplo  
 En este ejemplo, se establece un intervalo de muestreo de 1000 milisegundos para dos contadores de rendimiento de Windows.  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)