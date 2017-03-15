---
title: "LineOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# LineOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

De forma predeterminada, el generador de perfiles recoge datos de número de línea del código fuente y de desplazamiento del número de línea cuando se utiliza el método de generación de perfiles mediante muestreo.  La opción **LineOff** de VSPerfCmd deshabilita la recolección de datos de número de línea cuando se utiliza VSPerfCmd para iniciar la aplicación.  Cuando se especifica **LineOff**, los datos de generación de perfiles se recopilan en el nivel de función.  
  
 Solamente puede utilizar **LineOff** con la opción **Launch** y únicamente cuando el generador de perfiles se ha inicializado en el muestreo con la opción **Start**:**Sample**.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### Parámetros  
 None  
  
## Opciones necesarias  
 La opción **LineOff** solamente se puede utilizar en una línea de comandos que también contenga la opción **Launch**.  
  
 **Launch:** `AppName`  
 Inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.  
  
## Ejemplo  
 Este ejemplo inicia la aplicación y el generador de perfiles, y deshabilita el muestreo en el nivel de línea.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)