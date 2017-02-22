---
title: "WinCounter | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# WinCounter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **WinCounter** especifica un contador de rendimiento de aplicación o de Windows para recopilar a intervalos fijos durante la ejecución del perfil.  Los contadores de rendimiento de aplicación y de Windows se muestran como marcas en el archivo de datos de generación de perfiles.  Puede especificar varios contadores de rendimiento para recopilar en opciones independientes.  
  
 De forma predeterminada, los contadores se recopilan cada 500 milisegundos.  Utilice la opción **AutoMark** para especificar un intervalo de recolección diferente.  
  
 Solo se usa una opción **AutoMark**.  Si se especifica varias opciones **AutoMark**, se utiliza la última.  
  
 La opción **WinCounter** solamente se puede utilizar con la opción **Start**.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### Parámetros  
 `Path`  
 El contador de rendimiento de Windows en el formato de ruta de acceso de contador PDH.  
  
## Opciones necesarias  
 La opción **WinCounter** solamente se puede utilizar con la opción **Start**.  
  
 **Start:** `Method`  
 La opción **Start** inicializa el generador de perfiles al método de generación de perfiles especificado.  
  
## Opciones exclusivas  
 La opción **AutoMark** solamente se puede utilizar con la opción **WinCounter**.  
  
 **AutoMark:** `Milliseconds`  
 Especifica el número de milisegundos entre recolecciones de datos de rendimiento de Windows.  
  
## Ejemplo  
 En el ejemplo siguiente, se especifica que se recopilen dos contadores de rendimiento de Windows con un intervalo de 1000 milisegundos.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)