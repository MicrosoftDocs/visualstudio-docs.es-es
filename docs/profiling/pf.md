---
title: "PF | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# PF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **PF** de VSPerfCmd.exe establece el evento de generación de perfiles que se muestrea en errores de página, y cambia opcionalmente el número de errores de página en intervalo de muestreo respecto al valor predeterminado de 10.  
  
> [!NOTE]
>  PF no se puede utilizar en sistemas de 64 bits.  
  
 **Nota**  
 **PF** no se admite en equipos de 64 bits.**PF** solo se puede usar en una línea de comandos que también contenga la opción **Launch** o **Attach**.  
  
 De forma predeterminada, el evento de muestreo está establecido en los ciclos de reloj de procesador no detenidos y el intervalo del muestreo está establecido en 10.000.000.  Las opciones **Timer**, **PF**, **Sys** y **Counter** permiten establecer el evento de muestra y el intervalo de muestreo.  La opción **GC** recopila datos de memoria de .NET en cada evento de asignación y de recolección de elementos no utilizados.  Solamente se puede especificar una de estas opciones en una línea de comandos.  
  
 El evento de muestreo y el intervalo de muestreo solamente se pueden establecer en la primera línea de comandos que contiene una opción **Launch** o **Attach**.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### Parámetros  
 `Events`  
 Valor entero que especifica el número de eventos de error de página en un intervalo de muestreo.  Si no se especifica `Events`, el intervalo se establece en 10.  
  
## Opciones necesarias  
 **PF** solamente se puede especificar en una línea de comandos que contiene una de las opciones siguientes.  
  
 **Launch:** `AppName`  
 Inicia el generador de perfiles y la aplicación especificada por AppName.  
  
 **Attach:** `PID`  
 Adjunta el generador de perfiles al proceso especificado por AppName.  
  
## Opciones no válidas  
 Las opciones siguientes no se pueden especificar en la misma línea de comandos que **PF**.  
  
 **Timer**\[**:**`Cycles`\]  
 Establece el evento de muestreo en ciclos de reloj de procesador y, opcionalmente, establece el intervalo del muestreo en `Cycles`.  El intervalo predeterminado del temporizador es 10.000.000.  
  
 **Sys**\[**:**`Events`\]  
 Establece el evento de muestreo en las llamadas de la aplicación para la que se generan perfiles al kernel del sistema operativo \(syscalls\) y, opcionalmente, establece el intervalo de muestreo en `Events`.  El intervalo Sys predeterminado es 10.  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 Establece el evento de muestreo en el contador de rendimiento de la CPU especificado por `Name` y establece el intervalo de muestreo en `Reload`.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Recopila datos de memoria de .NET.  De forma predeterminada, \(**Allocation**\) se recopilan datos en cada evento de asignación de memoria.  Cuando se especifica el parámetro **Lifetime**, también se recopilan datos en cada evento de recolección de elementos no utilizados.  
  
## Ejemplo  
 En este ejemplo se muestra cómo establecer el evento de ejemplo de generación de perfiles en los errores de página y establecer el intervalo de muestreo en 20 errores de página.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)