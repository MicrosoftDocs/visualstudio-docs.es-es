---
title: "Salida | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Salida
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **Output** especifica el nombre y la ubicación del archivo de datos de generación de perfiles de la sesión de rendimiento.  **Output** debe usarse con la opción **Start**.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### Parámetros  
 `FileName`  
 Nombre del archivo de datos.  Se aceptan rutas de acceso completas y parciales.  Si no se especifica ninguna ruta de acceso, el archivo se crea en el directorio actual.  
  
## Opciones necesarias  
 La opción **Output** debe usarse con la opción **Start**.  
  
 **Start:** `Method`  
 Especifica el nombre del archivo de salida.  
  
## Ejemplo  
 En el siguiente ejemplo, el archivo de datos de generación de perfiles se crea en el directorio actual.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)