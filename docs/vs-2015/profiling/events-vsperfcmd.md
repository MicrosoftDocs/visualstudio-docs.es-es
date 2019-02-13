---
title: Events (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bcfd234f67245ee39e8ba278ec256ba68b158785
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800176"
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La opción **Events** de VSPerfCmd.exe controla el registro del Seguimiento de eventos para Windows (ETW). Los datos de ETW se guardan en un archivo .etl que es independiente del archivo de datos del generador de perfiles. Los datos se pueden ver en un informe mediante el comando [VSPerfReport](../profiling/vsperfreport.md) /summary:etw.  
  
 Se puede llamar a la opción **Events** en cualquier momento antes de que se llame al comando VSPerfCmd **Shutdown** para detener la generación de perfiles.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Parámetros  
 **On**&#124;**Off**  
 Inicia o detiene la recopilación de datos del evento.  
  
 `Guid`  
 El GUID del control del proveedor.  
  
 `ProviderName`  
 El nombre del proveedor que está registrado con el Instrumental de administración de Windows (WMI).  
  
 `Flags`  
 Un valor hexadecimal con prefijo "0x" marca el valor que se define mediante el proveedor de eventos.  
  
 `Level`  
 Especifica la cantidad de datos recopilados. `Level` se define mediante el proveedor de eventos.  
  
 La opción **Events** entiende las siguientes palabras clave de kernel como nombres de proveedor:  
  
 **Process**  
 Eventos de proceso  
  
 **Subproceso**  
 Eventos de subproceso  
  
 **Image**  
 Eventos de carga y descarga de imágenes  
  
 **Disk**  
 Eventos de E/S de disco  
  
 **Archivo**  
 Eventos de E/S de archivo  
  
 **Hardfault**  
 Errores de página en disco  
  
 **Pagefault**  
 Errores de página flexible  
  
 **Network**  
 Eventos de red  
  
 **Registry**  
 Eventos de acceso al Registro  
  
 Tenga en cuenta que el proveedor de kernel solo puede estar habilitado. No se puede deshabilitar, ni se pueden modificar sus marcas, hasta que se cierra el monitor.  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
>  Cuando se habilitan los eventos ETW de CLR, también se recopilan datos de inicio adicionales en el informe de vista de seguimiento. Para que no aparezcan eventos de inicio en el informe, use el comando siguiente:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Si no excluye los eventos de inicio, dado que estos eventos no se muestran en el archivo de Managed Object Format (MOF), se muestran como GUID en el informe. Para más información, vea esta página en el sitio web de Microsoft: [Sample Managed Object Format (MOF) File](http://go.microsoft.com/fwlink/?linkid=37118) [Archivo de ejemplo de Managed Object Format (MOF)].  
  
## <a name="see-also"></a>Vea también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles para aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles para aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generar perfiles de servicios](../profiling/command-line-profiling-of-services.md)
