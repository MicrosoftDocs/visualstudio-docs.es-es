---
title: Desasociar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b151e3ede34d0c8fa3a863d7a4e7474431ae6f4
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777395"
---
# <a name="detach"></a>Desasociar
La opción **Desasociar** de VSPerfCmd.exe desconecta el generador de perfiles de los procesos especificados o de todos los procesos si no se especifica ninguno. Se debe haber inicializado la generación de perfiles mediante el método de muestreo.

 La generación de perfiles que se ha iniciado con las opciones **Iniciar** o **Adjuntar** se puede desconectar con **Desasociar**. El generador de perfiles se puede volver a adjuntar mediante los comandos **Adjuntar** subsiguientes.

 **Desasociar** no cierra el archivo de datos de generación de perfiles. Use la opción **Cierre** para finalizar la generación de perfiles y cerrar el archivo de datos.

> [!NOTE]
> Si la opción **Start** se ha especificado con la opción **CrossSession**, en cualquier llamada a **VSPerfCmd /Attach** o a **VSPerfCmd /Detach** también se debe especificar **CrossSession**.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Parámetros
 `PIDs|ProcessNames` `PID`: identificador del sistema numérico de uno o varios procesos.

 `ProcessNames`: nombre del proceso. Si se ejecutan varias instancias del proceso designado, los resultados son imprevisibles.

 Separe varios procesos con comas.

 Si no se especifica ningún proceso, el generador de perfiles se desasocia de todos los procesos para los que se generan perfiles.

## <a name="valid-options"></a>Opciones válidas
 Las opciones siguientes de **VSPerfCmd** se pueden combinar con la opción **Adjuntar** en una sola línea de comandos.

 **Crosssession** Habilita la generación de perfiles de aplicaciones en las sesiones que no sean la sesión de inicio. Es obligatorio si la opción **Start** se ha especificado con la opción **CrossSession**.

## <a name="example"></a>Ejemplo
 En este ejemplo, el comando **Desasociar** suspende la generación de perfiles y el comando **Cierre** cierra el archivo de datos del generador de perfiles.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
