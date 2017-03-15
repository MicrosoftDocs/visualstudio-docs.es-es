---
title: "Iniciar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Iniciar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **Launch** inicia el generador de perfiles mediante el método de muestreo y también inicia la aplicación especificada.  
  
 Para utilizar la opción **Launch**, debe especificar el método **Sample** en la opción **Start**.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### Parámetros  
 `AppName`  
 Nombre de la aplicación que se va a iniciar.  Se admiten las rutas de acceso completas y parciales desde el directorio actual.  
  
## Opciones válidas  
 Las opciones de VSPerfCmd siguientes se pueden combinar con la opción **Launch** en una línea de comandos única.  
  
 **Start:** `Method`  
 Inicializa la sesión del generador de perfiles de línea de comandos y establece el método de generación de perfiles especificado.  
  
 **GlobalOn** y **GlobalOff**  
 Reanuda \(**GlobalOn**\) o pausa \(**GlobalOff**\), la generación de perfiles, pero no finaliza la sesión de generación de perfiles.  
  
 **ProcessOn:** `PID` y **ProcessOff**:`PID`  
 Reanuda \(**ProcessOn**\) o pausa \(**ProcessOff**\) la generación de perfiles para el proceso especificado.  
  
 **TargetCLR**  
 Especifica la versión del Common Language Runtime \(CLR\) de .NET Framework para la generación de perfiles cuando se carga más de una versión se carga en una sesión de generación de perfiles.  De forma predeterminada, se generan los perfiles de la primera versión cargada.  
  
## Opciones exclusivas  
 Las opciones siguientes solo se pueden utilizar con la opción **Launch**.  
  
 **Console**  
 Inicia la aplicación de línea de comandos especificada en una nueva ventana.  
  
 **Args:** `ArgList`  
 Especifica la lista de argumentos para pasar a la aplicación.  
  
 **LineOff**  
 Deshabilita la recolección de datos de generación de perfiles de nivel de línea.  
  
## Opciones de muestreo  
 Se puede especificar una de las siguientes opciones de intervalo de muestreo en la línea de comandos de **Launch**.  El intervalo de muestreo predeterminado es de 10.000.000 de ciclos de reloj de procesador.  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**`Events`\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]**GC**\[:**allocation**&#124;**lifetime**\]  
 Especifica el número y el tipo de intervalo de muestreo.  
  
-   **Timer**: muestrea cada `Cycles` ciclos de reloj de procesador no detenidos.  Si no se especifica `Cycles`, se utilizan 10.000.000 ciclos.  
  
-   **PF**: muestrea cada `Events` errores de página.  Si no se especifica `Events`, 10 errores de página.  
  
-   **Sys**: muestrea cada `Events` llamadas al sistema operativo.  Si no se especifica `Events`, se utilizan 10 llamadas al sistema.  
  
-   **Counter**: muestrea cada número `Reload` del contador de rendimiento de la CPU especificado por `Name`.  Opcionalmente, `FriendlyName` puede especificar una cadena para utilizarla como encabezado de columna en informes del generador de perfiles.  
  
-   **GC**: recopila datos de memoria de .NET.  De forma predeterminada \(**allocation**\), los datos se recopilan en cada evento de asignación de memoria.  Cuando se especifica el parámetro **lifetime**, también se recopilan datos en cada evento de recolección de elementos no utilizados.  
  
## Ejemplo  
 En este ejemplo se muestra el uso de **Launch** para iniciar una aplicación.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)