---
title: "ProcessOn y ProcessOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ProcessOn y ProcessOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los subcomandos **ProcessOff** y **ProcessOn** de VSPerfCmd.exe pausan y reanudan la generación de perfiles para los procesos especificados de una sesión de generación de perfiles de la línea de comandos.  **ProcessOff** detiene la generación de perfiles del proceso y **ProcessOn** inicia la generación de perfiles del proceso.  
  
 En la mayoría de los casos, se especifica **ProcessOn** o **ProcessOff** como la única opción en una línea de comandos de VSPerfCmd.exe, pero también se pueden combinar con los subcomandos **GlobalOn**, **GlobalOff**, **ThreadOn** y **ThreadOff**.  
  
 Los subcomandos **ProcessOff** y **ProcessOn** interactúan con los subcomandos **GlobalOff** y **GlobalOn**, que controlan la recolección de datos para todos los procesos en una sesión generación de perfiles de la línea de comandos, y los subcomandos **ThreadOff** y **ThreadOn**, que controlan la recolección de datos para un subproceso especificado.  
  
 Los subcomandos **ProcessOn** y **ProcessOff** también afectan al recuento de inicio\/parada de procesos manipulado por las funciones de la API del generador de perfiles.  
  
-   **ProcessOff** establece inmediatamente el contador de inicio\/parada de proceso en 0 y, en consecuencia, detiene la generación de perfiles.  
  
-   **ProcessOn** establece inmediatamente el contador de inicio\/parada de proceso en 1 y, en consecuencia, reanuda la generación de perfiles.  
  
 Para obtener más información, vea [APIs de herramientas de generación de perfiles](../profiling/profiling-tools-apis.md).  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### Parámetros  
 `PID`  
 Identificador entero del proceso que se va a iniciar o detener.  Los identificadores de proceso se muestran en la pestaña Proceso del Administrador de tareas de Windows.  
  
## Subcomandos necesarios  
 None  
  
## Subcomandos válidos  
 **ProcessOn** y **ProcessOff** se pueden especificar en líneas de comandos que también contienen los subcomandos siguientes.  
  
 **Start:** `Method`  
 Inicializa la sesión de generación de perfiles de línea de comandos y establece el método de generación de perfiles especificado.  
  
 **Launch:** `AppName`  
 Inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.  
  
 **Attach:** `PID`  
 Inicia la generación de perfiles del proceso especificado.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Se detiene o inicia la generación de perfiles para todos los procesos de una sesión de generación de perfiles de línea de comandos.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Detiene o inicia la generación de perfiles para el subproceso especificado \(solamente el método de instrumentación\).  
  
## Ejemplo  
 En este ejemplo, el subcomando **ProcessOff** se utiliza para recopilar datos de generación de perfiles para el inicio de la aplicación.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)