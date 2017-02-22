---
title: "Marca | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Marca
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **Mark** de VSPerfCmd.exe inserta la información especificada en el archivo de datos de generación de perfiles.  Se puede hacer una lista de Marca en un informe de VSPerfReport independiente o en la vista de informe Marca de la interfaz de usuario del generador de perfiles.  **Mark** se puede usar para especificar los puntos inicial y final en los filtros de informe y vista.  
  
 La opción **Mark** debe ser la única opción especificada en la línea de comandos.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]   
```  
  
#### Parámetros  
 `MarkID`  
 Entero definido por el usuario que se muestra como identificador de marca en las vistas e informes del generador de perfiles.  `MarkID` no tiene que ser único.  
  
 `MarkName`  
 \(Opcional\) Cadena definida por el usuario que se muestra como nombre de marca en las vistas y los informes del generador de perfiles.  Si no se especifica `MarkName`, el campo Nombre de marca de la lista de marcas aparece vacío.  Incluya las cadenas que contienen espacios o barras diagonales \("\/"\) entre comillas.  
  
## Ejemplo  
 En este ejemplo se inserta una marca con el identificador 123 y el nombre de marca "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)