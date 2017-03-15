---
title: "GC (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **GC** habilita la recolección de datos de asignación de memoria y de duración de objetos de .NET Framework.  La opción **GC** solamente se puede utilizar con el método de generación de perfiles mediante muestreo y únicamente con la opción **Launch**.  
  
 Si usa la opción **GC**, no se necesita el comando VSPerfClrEnv **\/sampleon**.  
  
 Si no se especifica ningún parámetro, o si se especifica el parámetro **Allocation**, solo se recopilan datos de asignación de memoria de .NET Framework.  Si se especifica el parámetro **Lifetime**, se recopilan datos de asignación de memoria de .NET Framework y datos de duración de objetos de .NET Framework.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### Parámetros  
 **Allocation**  
 Valor predeterminado.  Recopila datos de asignación de memoria de .NET Framework.  
  
 **Lifetime**  
 Recopila datos de asignación de memoria y datos de duración de objetos de .NET Framework.  
  
## Opciones necesarias  
 La opción **GC** solamente se puede utilizar con la opción **Launch**.  
  
 **Launch:** `AppName`  
 Inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.  
  
## Ejemplo  
 En el ejemplo siguiente se inicia una aplicación y se recopilan los datos de asignación de memoria de .NET Framework.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)