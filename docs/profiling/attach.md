---
title: "Asociar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Asociar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **Attach** de VSPerfCmd.exe inicia la generación de perfiles de muestra de los procesos en ejecución que se especifican mediante el identificador de proceso \(PID\).  
  
 Para utilizar la opción **Attach**, debe especificar el método **Sample** en la opción Start.  
  
> [!NOTE]
>  Si la opción **Start** se especificó con la opción **Crosssession**, cualquier llamada a **VSPerfCmd \/Attach** o a **VSPerfCmd \/Detach** también debe especificar **Crosssession**.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### Parámetros  
 `ProcessID`  
 Identificador de proceso \(PID\) del proceso en ejecución.  El PID de un proceso en ejecución se muestra en la pestaña Procesos del Administrador de tareas de Windows.  
  
## Opciones válidas  
 Las opciones **VSPerfCmd** siguientes se pueden combinar con la opción **Attach** en una línea de comandos única.  
  
 **Crosssession**  
 Habilita la generación de perfiles de aplicaciones en sesiones distintas del inicio de sesión.  Necesaria si se especificó la opción **Start** con la opción **Crosssession**.  
  
 **Start:** `Method`  
 Inicializa la sesión del generador de perfiles de línea de comandos y establece el método de generación de perfiles especificado.  
  
 **TargetCLR**  
 Especifica la versión del Common Language Runtime \(CLR\) de .NET Framework para la generación de perfiles cuando se carga más de una versión se carga en una sesión de generación de perfiles.  De forma predeterminada, se generan los perfiles de la primera versión cargada.  
  
 **GlobalOn GlobalOff**  
 Reanuda \(**GlobalOn**\) o pausa \(**GlobalOff**\), la generación de perfiles, pero no finaliza la sesión de generación de perfiles.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Reanuda \(**ProcessOn**\) o pausa \(**ProcessOff**\) la generación de perfiles para el proceso especificado.  
  
## Opciones de Intervalo  
 Se puede especificar una de las siguientes opciones de intervalo de muestreo en la línea de comandos de Attach.  El intervalo de muestreo predeterminado es de 10.000.000 de ciclos de reloj de procesador.  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**Events\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]  
 Especifica el número y el tipo de intervalo de muestreo.  
  
-   **Timer**: muestras cada número `Cycles` de ciclos de reloj de procesador.  Si no se especifica `Cycles`, se utilizan 10.000.000 ciclos.  
  
-   **PF**: muestrea cada `Events` errores de página.  Si no se especifica `Events`, se utilizan 10 errores de página.  
  
-   **Sys**: muestrea cada `Events` llamadas al sistema operativo.  Si no se especifica `Events`, se utilizan 10 llamadas al sistema.  
  
-   **Counter**: muestrea cada número `Reload` del contador de rendimiento de la CPU especificado por `Name`.  Opcionalmente, `FriendlyName` puede especificar una cadena para utilizarla como encabezado de columna en informes del generador de perfiles.  
  
## Ejemplo  
 En este ejemplo se muestra cómo se adjunta a una instancia en ejecución de una aplicación con el identificador de proceso 12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)