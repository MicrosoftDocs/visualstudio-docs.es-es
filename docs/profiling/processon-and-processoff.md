---
title: ProcessOn y ProcessOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 62c16c2d578a38187b4a58958466597a5e4d297d
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778393"
---
# <a name="processon-and-processoff"></a>ProcessOn y ProcessOff
Los subcomandos **ProcessOff** y **ProcessOn** de VSPerfCmd.exe pausan y reanudan la generación de perfiles para el proceso especificado en una sesión de generación de perfiles de línea de comandos. **ProcessOff** detiene el proceso de generación de perfiles y **ProcessOn** inicia el proceso de generación de perfiles.

 En la mayoría de los casos, se especifica **ProcessOn** o **ProcessOff** como la única opción en una línea de comandos de VSPerfCmd.exe, pero también se pueden combinar con los subcomandos **GlobalOn**, **GlobalOff**, **ThreadOn** y **ThreadOff**.

 Los subcomandos **ProcessOn** y **ProcessOff** interactúan con los subcomandos **GlobalOn** y **GlobalOff** que controlan la recopilación de datos para todos los procesos de una sesión de generación de perfiles de línea de comandos, y con los subcomandos **ThreadOn** y **ThreadOff** que controlan la recopilación de datos para un proceso especificado.

 Los subcomandos **ProcessOff** y **ProcessOn** también afectan al recuento de inicios y paradas de procesos que se manipula mediante las funciones de API del generador de perfiles.

- **ProcessOff** establece inmediatamente el contador de inicio/parada de procesos en 0 y, en consecuencia, pausa la generación de perfiles.

- **ProcessOn** establece inmediatamente el contador de inicio/parada de procesos en 1 y, en consecuencia, reanuda la generación de perfiles.

  Para más información, vea [API de herramientas de generación de perfiles](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]

```

#### <a name="parameters"></a>Parámetros
 `PID` Identificador de entero del proceso que se va a iniciar o detener. Los identificadores de proceso se muestran en la pestaña **Proceso** del Administrador de tareas de Windows.

## <a name="required-subcommands"></a>Subcomandos necesarios
 None

## <a name="valid-subcommands"></a>Subcomandos válidos
 **ProcessOn** y **ProcessOff** se pueden especificar en líneas de comandos que también contienen los subcomandos siguientes.

 **Start:** `Method` Inicializa la sesión de generación de perfiles de línea de comandos y establece el método de generación de perfiles especificado.

 **Launch:** `AppName` Inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.

 **Attach:** `PID` Inicia la generación de perfiles del proceso especificado.

 **GlobalOff**&#124;**GlobalOn** Detiene o inicia la generación de perfiles para todos los procesos en una sesión de generación de perfiles de línea de comandos.

 {**ThreadOff**&#124;**ThreadOn**} **:** `TID` Detiene o inicia la generación de perfiles para el subproceso especificado (solo método de instrumentación).

## <a name="example"></a>Ejemplo
 En este ejemplo, el subcomando **ProcessOff** se usa para recopilar datos de generación de perfiles para el inicio de la aplicación.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the process after startup.
VSPerfCmd.exe /ProcessOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
