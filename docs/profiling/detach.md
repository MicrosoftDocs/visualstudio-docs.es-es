---
title: "Desasociar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Desasociar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción de VSPerfCmd.exe **Detach** desconecta el generador de perfiles de los procesos especificados o de todos los procesos, si no se especificó ninguno.  La generación de perfiles se debe haber inicializado utilizando el método de muestreo.  
  
 La generación de perfiles que se inicia con las opciones **Launch** o **Attach** se puede desconectar con **Detach**.  El generador de perfiles se puede volver a adjuntar utilizando subsiguientes comandos **Attach**.  
  
 **Detach** no cierra el archivo de datos de generación de perfiles.  Utilice la opción **Shutdown** para finalizar la generación de perfiles y cerrar el archivo de datos.  
  
> [!NOTE]
>  Si la opción **Start** se especificó con la opción **Crosssession**, cualquier llamada a **VSPerfCmd \/Attach** o a **VSPerfCmd \/Detach** también debe especificar **Crosssession**.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### Parámetros  
 `PIDs|ProcessNames`  
 `PID`\- El identificador numérico del sistema de uno o más procesos.  
  
 `ProcessNames`: nombre del proceso.  Si hay varias instancias del proceso con nombre en ejecución, los resultados son impredecibles.  
  
 Separe los diversos procesos con comas.  
  
 Si no se especifica ningún proceso, el generador de perfiles se desasocia de todos los procesos para los que se generó perfiles.  
  
## Opciones válidas  
 Las opciones **VSPerfCmd** siguientes se pueden combinar con la opción **Attach** en una línea de comandos única.  
  
 **Crosssession**  
 Habilita la generación de perfiles de aplicaciones en sesiones distintas del inicio de sesión.  Necesaria si se especificó la opción **Start** con la opción **Crosssession**.  
  
## Ejemplo  
 En este ejemplo, el comando **Detach** suspende la generación de perfiles y el comando **Shutdown** cierra el archivo de datos del generador de perfiles.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)