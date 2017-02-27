---
title: "Events (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Events (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La opción de VSPerfCmd.exe **Events** controla el registro de Seguimiento de eventos para Windows \(ETW\).  Los datos de ETW se guardan en un archivo .etl que es independiente del archivo de datos del generador de perfiles.  Los datos se pueden ver en un informe utilizando el comando [VSPerfReport](../profiling/vsperfreport.md) \/summary:etw.  
  
 Se puede llamar a la opción **Events** en cualquier momento antes de llamar al comando **Shutdown** de VSPerfCmd para detener la generación de perfiles.  
  
## Sintaxis  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### Parámetros  
 **On**&#124;**Off**  
 Inicia o detiene la recolección de datos de evento.  
  
 `Guid`  
 GUID del control del proveedor.  
  
 `ProviderName`  
 Nombre del proveedor registrado con Instrumental de administración de Windows \(WMI\).  
  
 `Flags`  
 Valor de marcas hexadecimales con el prefijo "0x" definido por el proveedor de eventos.  
  
 `Level`  
 Especifica la cantidad de datos recolectados.  `Level` lo define el proveedor de eventos.  
  
 La opción **Events** entiende las siguientes palabras clave de kernel como nombres de proveedor:  
  
 **Process**  
 Eventos de proceso  
  
 **Thread**  
 Eventos de subproceso  
  
 **Image**  
 Eventos de carga y descarga de imágenes  
  
 **Disk**  
 Eventos de E\/S de disco  
  
 **File**  
 Eventos de E\/S de archivos  
  
 **Hardfault**  
 Errores de página en disco  
  
 **Pagefault**  
 Errores de página en memoria  
  
 **Network**  
 Eventos de red  
  
 **Registry**  
 Eventos de acceso al Registro  
  
 Tenga en cuenta que el proveedor de kernel sólo puede estar habilitado.  No se puede deshabilitar, ni se puede modificar sus marcadores, hasta que el monitor se cierre.  
  
## Comentarios  
  
> [!NOTE]
>  Cuando están habilitados los eventos ETW de CLR, también se recopilan datos de inicio adicionales en el informe de seguimiento.  Para excluir los eventos de inicio de modo que no aparezcan en el informe, utilice el comando siguiente:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Si no excluye los eventos de inicio, al no aparecer en el archivo de formato de objetos no administrados \(MOF\) aparecerán como GUID en el informe.  Para obtener más información, vea esta página en el sitio web de Microsoft: [Archivo de \(MOF\) de Formato de objetos administrados de ejemplo](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Servicios de generación de perfiles](../profiling/command-line-profiling-of-services.md)