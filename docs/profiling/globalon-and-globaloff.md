---
title: GlobalOn y GlobalOff | Microsoft Docs
description: Revise las opciones GlobalOn y GlobalOff en VSPerfCmd.exe. Estas opciones pausan y reanudan la generación de perfiles de procesos y subprocesos en una sesión de generación de perfiles de la línea de comandos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: eaeac096c6bdff77368508bd34276d66530fa739
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801343"
---
# <a name="globalon-and-globaloff"></a>GlobalOn y GlobalOff
Las opciones **GlobalOff** y **GlobalOn** de *VSPerfCmd.exe* pausan y reanudan la generación de perfiles para todos los procesos y subprocesos de una sesión de generación de perfiles de la línea de comandos.

 Puede especificar **GlobalOn** y **GlobalOff** como únicas opciones en una línea de comandos de *VSPerfCmd.exe* o bien puede incluirlas en líneas de comandos que también contengan las opciones **Start**, **Launch** o **Attach**.

 **GlobalOn** y **GlobalOff** también se pueden combinar con las opciones **ProcessOn**, **ProcessOff**, **ThreadOn** y **ThreadOff**.

 Las opciones **GlobalOn** y **GlobalOff** interactúan con las opciones **ProcessOn** y **ProcessOff** que controlan la recopilación de datos para un proceso especificado, y con las opciones **ThreadOn** y **ThreadOff** que controlan la recopilación de datos para un subproceso especificado.

 Las opciones **GlobalOn** y **GlobalOff** también afectan al recuento de inicio/parada global manipulado por las funciones de la API del generador de perfiles.

- **GlobalOff** establece inmediatamente el contador de inicio/parada global en 0 y, en consecuencia, detiene la generación de perfiles.

- **GlobalOn** establece inmediatamente el contador de inicio/parada global en 1 y, en consecuencia, reanuda la generación de perfiles.

  Para obtener más información, vea [API de herramientas de generación de perfiles](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /{GlobalOff|GlobalOn}

VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]

VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]
```

#### <a name="parameters"></a>Parámetros
 None

## <a name="valid-options"></a>Opciones válidas
 **GlobalOn** y **GlobalOff** se pueden especificar en líneas de comandos que también contienen las siguientes opciones.

 **Start:** `Method` Inicializa la sesión del generador de perfiles de línea de comandos y establece el método de generación de perfiles especificado.

 **Launch:** `AppName` Inicia la aplicación especificada y comienza la generación de perfiles con el método de muestreo.

 **Attach:** `PID` Inicia la generación de perfiles del proceso especificado.

 {**ProcessOff**&#124;**ProcessOn**} **:** `PID` Detiene o inicia la generación de perfiles para el proceso especificado.

 {**ThreadOff**&#124;**ThreadOn**} **:** `TID` Detiene o inicia la generación de perfiles para el proceso especificado (solo método de instrumentación).

## <a name="example"></a>Ejemplo
 En este ejemplo, las opciones **GlobalOff** y **GlobalOn** se utilizan para evitar la recopilación de datos de generación de perfiles para el inicio y el cierre de la aplicación.

```cmd
; Initialize the profiler with profiling stopped.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff
; Start an instrumented application and wait for it to warm up.
; Start profiling.
VSPerfCmd.exe /GlobalOn
; Exercise the application functionality that you want to profile.
; Stop profiling.
VSPerfCmd.exe /GlobalOff
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
