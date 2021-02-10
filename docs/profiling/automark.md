---
title: AutoMark | Microsoft Docs
description: Use la opción AutoMark para especificar un intervalo de tiempo entre los eventos de recopilación de datos de contadores de rendimiento de Windows. Úsela junto con la opción WinCounter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3712246256618debfb8d85ebfb0c273511eb9558
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901080"
---
# <a name="automark"></a>AutoMark
La opción **AutoMark** especifica el número de milisegundos entre la colección de eventos de los contadores de rendimiento de software de Windows. Los contadores de rendimiento de Windows se especifican en la opción **WinCounter**.

 Solo se puede especificar una opción **AutoMark** en la línea de comandos. Tenga en cuenta que el intervalo de muestreo de **WinCounter** especificado por **AutoMark** es independiente del intervalo de muestreo principal.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds
```

#### <a name="parameters"></a>Parámetros
 `Milliseconds` Especifica el número de milisegundos entre las colecciones de eventos de los contadores de rendimiento de Windows.

## <a name="required-options"></a>Opciones necesarias
 **WinCounter:** `Path` Especifica el contador de rendimiento de Windows que se va a recopilar. Cuando se usa el método de instrumentación, se pueden especificar varios contadores de Windows. Cuando se usa el método de muestreo, solo se puede especificar un contador de Windows. La opción **WinCounter** debe especificarse en una línea de comandos que contenga la opción **Start**.

## <a name="example"></a>Ejemplo
 En este ejemplo, se establece un intervalo de muestreo de 1000 milisegundos para dos contadores de rendimiento de Windows.

```cmd
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
