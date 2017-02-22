---
title: "ThreadOn y ThreadOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ThreadOn y ThreadOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los subcomandos VSPerfCmd.exe **ThreadOff** y **ThreadOn** sólo están disponibles en las sesiones de generación de perfiles de la línea de comandos que usan el método de instrumentación.  **ThreadOff** y **ThreadOn** realizan una pausa y reanudan la generación de perfiles para el subproceso especificado.  **ThreadOff** detiene la generación de perfiles del subproceso y **ThreadOn** inicia la generación de perfiles del subproceso.  
  
 En la mayoría de los casos, especifica **ThreadOn** o **ThreadOff** como única opción en una línea de comandos de VSPerfCmd.exe, pero también se pueden combinar con los subcomandos **GlobalOn**, **GlobalOff**, **ProcessOn** y **ProcessOff**.  
  
 Los subcomandos **ThreadOn** y **ThreadOff** interactúan con los subcomandos **GlobalOn** y **GlobalOff**, que controlan la recolección de datos para todos los procesos en una sesión de generación de perfiles de la línea de comandos, y los subcomandos **ProcessOn** y **ProcessOff**, que controlan la recolección de datos para un proceso especificado.  
  
 Los subcomandos **ThreadOff** y **ThreadOn** también afectan al recuento de inicio\/parada de subprocesos manipulado por las funciones de la API del generador de perfiles.  
  
-   **ThreadOff** establece inmediatamente el contador de inicio\/parada del subproceso en 0 y, en consecuencia, pausa la generación de perfiles.  
  
-   **ThreadOn** establece inmediatamente el contador de inicio\/parada del subproceso en 1 y, en consecuencia, reanuda la generación de perfiles.  
  
 Para obtener más información, vea [APIs de herramientas de generación de perfiles](../profiling/profiling-tools-apis.md).  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### Parámetros  
 `TID`  
 Identificador entero del subproceso que se va a iniciar o detener.  
  
## Opciones válidas  
 **ThreadOn** y **ThreadOff** se pueden especificar en líneas de comandos que también contienen los subcomandos siguientes.  
  
 **Start:** `Method`  
 Inicializa la sesión de generación de perfiles de línea de comandos y establece el método de generación de perfiles especificado.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Se detiene o inicia la generación de perfiles para todos los procesos de una sesión de generación de perfiles de línea de comandos.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 Detiene o inicia la generación de perfiles para el proceso especificado.  
  
## Ejemplo  
 En este ejemplo, se utiliza el subcomando **ThreadOff** para detener la recolección de datos de generación de perfiles de forma que solamente se recopilan datos de inicio de la aplicación.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)