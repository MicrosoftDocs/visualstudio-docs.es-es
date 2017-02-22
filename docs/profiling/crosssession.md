---
title: "CrossSession | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CrossSession
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción de VSPerfCmd.exe **CrossSession** permite al generador de perfiles recopilar datos de cualquier sesión de consola.  La opción **CrossSession** debe usarse con la opción **Start**.  
  
 Puede utilizar la abreviatura **CS** en lugar de **CrossSession**.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### Parámetros  
 None  
  
## Opciones válidas  
 Para habilitar la generación de perfiles en otra sesión, la opción **CrossSession** se debe especificar con la opción **Start**.  **CrossSession** también se debe especificar en cualquiera de los comandos subsiguientes **Detach** y **VSPerfCmd Attach**.  
  
 **Start:** `Method`  
 La opción **Start** inicializa el generador de perfiles al método de generación de perfiles especificado.  
  
 **Attach:** *PID*\[**,***PID*\]  
 Inicia la generación de perfiles de los procesos especificados.  
  
 **Detach**\[**:***PID*\[,*PID*\]\]  
 Detiene la generación de perfiles de los procesos especificados.  
  
## Ejemplo  
 En este ejemplo, la opción **CrossSession** se utiliza para adjuntar a una aplicación que se inició en otra sesión de consola.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)