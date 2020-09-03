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
ms.openlocfilehash: 0d24fc7a01a8eebe356f37704c1a821332f5dca1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850762"
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
  
 **Proceso**  
 Proceso de eventos  
  
 **Subproceso**  
 Eventos de subproceso  
  
 **Imagen**  
 Eventos de carga y descarga de imágenes  
  
 **Disco**  
 Eventos de E/S de disco  
  
 **Archivo**  
 Eventos de E/S de archivo  
  
 **Hardfault**  
 Errores de página en disco  
  
 **Pagefault**  
 Errores de página flexible  
  
 **Network**  
 Eventos de red  
  
 **Registro**  
 Eventos de acceso al Registro  
  
 Tenga en cuenta que el proveedor de kernel solo puede estar habilitado. No se puede deshabilitar, ni se pueden modificar sus marcas, hasta que se cierra el monitor.  
  
## <a name="remarks"></a>Observaciones  
  
> [!NOTE]
> Cuando se habilitan los eventos ETW de CLR, también se recopilan datos de inicio adicionales en el informe de vista de seguimiento. Para que no aparezcan eventos de inicio en el informe, use el comando siguiente:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
> Si no excluye los eventos de inicio, dado que estos eventos no se muestran en el archivo de Managed Object Format (MOF), se muestran como GUID en el informe. Para obtener más información, vea esta página en el sitio web de Microsoft: [archivo de ejemplo Managed Object Format (MOF)](https://msdn.microsoft.com/library/default.aspx).  
  
## <a name="see-also"></a>Consulte también  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Generar perfiles de aplicaciones Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Generación de perfiles de servicios](../profiling/command-line-profiling-of-services.md)
