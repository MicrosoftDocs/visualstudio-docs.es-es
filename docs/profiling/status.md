---
title: "Estado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Estado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción **Status** de VSPerfCmd.exe muestra información sobre el estado de generador de perfiles y sobre los procesos para los que se esté generando perfiles actualmente.  
  
 La opción **Status** debe ser la única opción especificada en la línea de comandos.  El generador de perfiles se debe inicializar con la opción de VSPerfCmd.exe **Start** antes de que se pueda mostrar cualquier estado.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### Parámetros  
 None  
  
## Comentarios  
 La opción **Status** muestra la información de estado siguiente para el generador de perfiles.  
  
 **Output File Name**  
 Ruta de acceso y nombre de archivo de datos actual del generador de perfiles.  
  
 **Collection Mode**  
 SAMPLE o TRACE  
  
 **Maximum Processes**  
 El número máximo de procesos para los que se puede generar perfiles a la vez y el número de procesos actualmente activos.  
  
 **Maximum Threads**  
 El número máximo de subprocesos para los que se puede generar perfiles a la vez.  
  
 **Number of Buffers**  
 El número de búferes de memoria dedicados a escribir datos de generación de perfiles.  
  
 **Size of Buffers**  
 El tamaño en bytes de un búfer de memoria.  
  
 La opción **Status** muestra la información de estado siguiente para cada proceso para el que se esté generando perfiles actualmente.  
  
 **Process**  
 Nombre del proceso para el que se esté generando perfiles.  
  
 **Process ID**  
 Identificador del sistema del proceso.  
  
 **Num Threads**  
 Número de subprocesos actualmente en ejecución.  
  
 **Start\/Stop Count**  
 Recuento del generador de perfiles interno principal para controlar la recolección de datos para este proceso.  El recuento debe ser igual a uno para recopilar datos.  Las API del generador de perfiles y las opciones **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**y **ThreadOff** de VSPerfCmd pueden manipular el recuento de Inicio\/Parada.  
  
 **Suspend\/Resume Count**  
 Recuento del generador de perfiles interno secundario para controlar la recolección de datos para este proceso.  El recuento debe ser menor o igual que cero para recopilar datos.  Solamente las API del generador de perfiles pueden manipular el recuento **Suspend\/Resume**.  
  
 **Users with access rights to monitor**  
 Muestra una lista de los nombres de usuario que tienen acceso al generador de perfiles.  Se puede conceder acceso a usuarios adicionales utilizando la opción **Admin** de VSPerfCmd.exe.  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)