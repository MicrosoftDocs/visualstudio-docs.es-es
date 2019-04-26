---
title: Events (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62d4e2431ab2dbc2ca74944ac1717fe6c3169287
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440093"
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
La opción **Events** de *VSPerfCmd.exe* controla el registro del Seguimiento de eventos para Windows (ETW). Los datos de ETW se guardan en un archivo .etl que es independiente del archivo de datos del generador de perfiles. Los datos se pueden ver en un informe mediante el comando [VSPerfReport](../profiling/vsperfreport.md) /summary:etw.

 Se puede llamar a la opción **Events** en cualquier momento antes de que se llame al comando VSPerfCmd **Shutdown** para detener la generación de perfiles.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Parámetros
 **On**&#124;**Off** Inicia o detiene la recopilación de datos del evento.

 `Guid` El GUID del control del proveedor.

 `ProviderName` El nombre del proveedor que está registrado con el Instrumental de administración de Windows (WMI).

 `Flags` Un valor hexadecimal con prefijo "0x" marca el valor que se define mediante el proveedor de eventos.

 `Level` Especifica la cantidad de datos recopilados. `Level` se define mediante el proveedor de eventos.

 La opción **Events** entiende las siguientes palabras clave de kernel como nombres de proveedor:

 **Process** Eventos de proceso

 **Thread** Eventos de subprocesos

 **Image** Eventos de carga y descarga de imágenes

 **Disk** Eventos de E/S de disco

 **File** Eventos de E/S de archivo

 **Hardfault** Errores de página en disco

 **Hardfault** Errores de página en disco

 **Network** Eventos de red

 **Registry** Eventos de acceso al Registro

 Tenga en cuenta que el proveedor de kernel solo puede estar habilitado. No se puede deshabilitar, ni se pueden modificar sus marcas, hasta que se cierra el monitor.

## <a name="remarks"></a>Comentarios

> [!NOTE]
> Cuando se habilitan los eventos ETW de CLR, también se recopilan datos de inicio adicionales en el informe de vista de seguimiento. Para que no aparezcan eventos de inicio en el informe, use el comando siguiente:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Si no excluye los eventos de inicio, dado que estos eventos no se muestran en el archivo de Managed Object Format (MOF), se muestran como GUID en el informe. Para obtener más información, vea esta página en el sitio web de Microsoft: [Sample Managed Object Format (MOF) file](http://go.microsoft.com/fwlink/?linkid=37118) (Archivo Managed Object Format (MOF) de ejemplo).

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)