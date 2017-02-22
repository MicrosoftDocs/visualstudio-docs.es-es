---
title: "Consola | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Consola
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción de VSPerfCmd.exe **Console** inicia la aplicación especificada en una nueva ventana del símbolo del sistema.  **Console** solamente se puede usar con la opción VSPerfCmd **Launch**.  Si la aplicación no es una aplicación de línea de comandos, **Console** no tiene ningún efecto.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### Parámetros  
 None  
  
## Opciones necesarias  
 **Console** solo se puede especificar en una línea de comandos que también contenga la opción **Launch**.  
  
 **Launch:** `AppName`  
 Inicia el generador de perfiles y la aplicación especificada por `AppName`.  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)