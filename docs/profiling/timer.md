---
title: "Timer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Timer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **Timer** de VSPerfCmd.exe establece el evento de generación de perfiles que se muestrea en ciclos de reloj del procesador, y cambia opcionalmente el número de ciclos en un intervalo de muestreo respecto al valor predeterminado de 10.000.000. En un procesador de 1 GH \(un giga\), 10.000.000 ciclos de reloj representan aproximadamente 100 muestras por segundo. El número mínimo de ciclos que se puede especificar es 50.000.  
  
 **Timer** solamente se puede usar cuando se utiliza el método de generación de perfiles mediante muestreo y únicamente se puede usar en una línea de comandos que también contenga las opciones **Launch** o **Attach**.  
  
 De forma predeterminada, el evento de muestreo del generador de perfiles está establecido en los ciclos de reloj de procesador y el intervalo de muestreo está establecido en 10.000.000. Las opciones **Timer**, **PF**, **Sys** y **Counter** permiten establecer el evento de muestreo y el intervalo de muestreo. La opción **GC** recopila datos de memoria de .NET en cada evento de asignación y de recolección de elementos no utilizados. Solamente se puede especificar una de estas opciones en una línea de comandos.  
  
 El evento de muestreo y el intervalo de muestreo solamente se pueden establecer en la primera línea de comandos que contenga las opciones **Launch** o **Attach**.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### Parámetros  
 `Cycles`  
 Valor entero que especifica el número de ciclos de reloj del procesador en un intervalo de muestreo. Si no se especifica `Cycles`, el intervalo se establece en 10.000.000. Especifique el valor sin puntos.  
  
## Opciones necesarias  
 **Timer** solamente se puede especificar en una línea de comandos que contenga una de las opciones siguientes.  
  
 **Launch:** `AppName`  
 Inicia el generador de perfiles y la aplicación especificada por `AppName`.  
  
 **Attach:** `PID`  
 Asocia el generador de perfiles al proceso especificado por el identificador de proceso \(`PID`\).  
  
## Opciones no válidas  
 Las opciones siguientes no se pueden especificar en la misma línea de comandos que **Timer**.  
  
 **PF**\[**:**`Events`\]  
 Establece el evento de muestreo en los errores de página y, opcionalmente, establece el intervalo del muestreo en `Events`. El intervalo PF predeterminado es 10.  
  
 **Sys**\[**:**`Events`\]  
 Establece el evento de muestreo en las llamadas al sistema operativo y, opcionalmente, establece el intervalo del muestreo en `Events`. El intervalo Sys predeterminado es 10.  
  
 **Counter**\[**:**`Name,Reload,FriendlyName`\]  
 Establece el evento de muestreo en el contador de rendimiento de la CPU especificado por `Name` y establece el intervalo de muestreo en `Reload`.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Recopila datos de memoria de .NET. Mediante la opción \(**Allocation**\) predeterminada, se recopilan datos en cada evento de asignación de memoria. Cuando se especifica el parámetro **Lifetime**, también se recopilan datos en cada evento de recolección de elementos no utilizados.  
  
## Ejemplo  
 En este ejemplo se muestra cómo establecer el intervalo de muestreo del generador de perfiles en 1.000.000 ciclos de procesador.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)